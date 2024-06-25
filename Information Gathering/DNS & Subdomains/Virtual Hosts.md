Depois que o DNS direciona o tráfego para o servidor correto, a configuração do servidor web torna-se crucial para determinar como as solicitações recebidas são tratadas. Servidores Web como Apache, Nginx ou IIS são projetados para hospedar vários sites ou aplicativos em um único servidor. Eles conseguem isso por meio de hospedagem virtual, que lhes permite diferenciar domínios, subdomínios ou até mesmo sites separados com conteúdos distintos.

## Como Funcionam os Hosts Virtuais: Entendendo VHosts e Subdomínios

### Subdomínios

Subdomínios são extensões de um nome de domínio principal. Por exemplo, `blog.example.com` é um subdomínio de `example.com`. Subdomínios normalmente têm seus próprios registros DNS que podem apontar para o mesmo endereço IP do domínio principal ou para um endereço diferente. Eles são usados para organizar diferentes seções ou serviços de um site.

### Virtual Hosts (VHosts)

Hosts virtuais são configurações dentro de um servidor web que permitem hospedar vários sites ou aplicações em um único servidor. Eles podem ser associados a domínios de nível superior (por exemplo, `example.com`) ou subdomínios (por exemplo, `dev.example.com`). Cada host virtual pode ter sua própria configuração separada, permitindo controle preciso sobre como as solicitações são tratadas.

Se um host virtual não tiver um registro DNS, você ainda poderá acessá-lo modificando o arquivo `hosts` em sua máquina local. Este arquivo permite mapear manualmente um nome de domínio para um endereço IP, ignorando a resolução DNS.

### Exemplo de Configuração de VHosts no Apache

<VirtualHost *:80>
    ServerName www.example1.com
    DocumentRoot /var/www/example1
</VirtualHost>

<VirtualHost *:80>
    ServerName www.example2.org
    DocumentRoot /var/www/example2
</VirtualHost>

<VirtualHost *:80>
    ServerName www.another-example.net
    DocumentRoot /var/www/another-example
</VirtualHost>


Neste exemplo, `example1.com`, `example2.org` e `another-example.net` são domínios distintos hospedados no mesmo servidor. O servidor web usa o cabeçalho `Host` para fornecer o conteúdo apropriado com base no nome de domínio solicitado.

## Tipos de Hospedagem Virtual

### Name-Based Virtual Hosting

Este método depende do cabeçalho `Host` HTTP para distinguir entre sites. É o método mais comum e flexível, pois não requer vários endereços IP. É econômico, fácil de configurar e suporta a maioria dos servidores web modernos. No entanto, pode ter limitações com certos protocolos como SSL/TLS.

### IP-Based Virtual Hosting

Este tipo de hospedagem atribui um endereço IP exclusivo para cada site hospedado no servidor. O servidor determina qual site servir com base no endereço IP para o qual a solicitação foi enviada. Não depende do cabeçalho `Host`, pode ser usado com qualquer protocolo e oferece melhor isolamento entre sites. No entanto, requer vários endereços IP, o que pode ser caro e menos escalável.

### Port-Based Virtual Hosting

Sites diferentes estão associados a portas diferentes no mesmo endereço IP. Por exemplo, um site pode estar acessível na porta 80, enquanto outro está na porta 8080. É usado quando os endereços IP são limitados, mas não é tão comum quanto a hospedagem virtual baseada em nome e pode exigir que os usuários especifiquem o número da porta no URL.

## Ferramentas de Descoberta de Host Virtual

### Gobuster

Gobuster é uma ferramenta versátil comumente usada para força bruta de diretórios e arquivos, mas também é excelente na descoberta de hosts virtuais. Ele envia sistematicamente solicitações HTTP com diferentes cabeçalhos `Host` para um endereço IP de destino e analisa as respostas para identificar hosts virtuais válidos.

#### Comando para VHosts de Força Bruta

`$ gobuster vhost -u http://<target_IP_address> -w <wordlist_file> --append-domain`

- `-u`: especifica o URL de destino (substitua `<target_IP_address>` pelo IP real).
- `-w`: especifica o arquivo da lista de palavras (substitua `<wordlist_file>` pelo caminho para sua lista de palavras).
- `--append-domain`: anexa o domínio base a cada palavra na lista de palavras.

#### Exemplo de Uso do Gobuster

`$ gobuster vhost -u http://exemplo.htb:81 -w /usr/share/SecLists/Discovery/DNS/subdomains-top1million-110000.txt --append-domain =============================================================Gobuster v3.6 
`by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart) =============================================================[+] Url:             http://inlanefreight.htb:81 
`[+] Method:          
`GET [+] Threads:         10 [+] Wordlist:        /usr/share/SecLists/Discovery/DNS/subdomains-top1million-110000.txt
`[+] User Agent:      gobuster/3.6 
`[+] Timeout:         10s 
`[+] Append Domain:   true ==================================================
`Starting gobuster in VHOST enumeration mode 
`==================================================
`Found: forum.inlanefreight.htb:81 Status: 200 [Size: 100] [...] 
`Progress: 114441 / 114442 (100.00%) 
`================================================== 
`Finished 
`==================================================

Gobuster gerará hosts virtuais em potencial à medida que os descobre. Analise os resultados cuidadosamente, observando quaisquer descobertas incomuns ou interessantes. Poderá ser necessária uma investigação mais aprofundada para confirmar a existência e a funcionalidade dos hosts virtuais descobertos.

#### Argumentos Adicionais Úteis no Gobuster

- `-t`: aumenta o número de threads para uma verificação mais rápida.
- `-k`: ignora erros de certificado SSL/TLS.
- `-o`: salva a saída em um arquivo para análise posterior.

Utilizando essas ferramentas e técnicas, você pode descobrir hosts virtuais e subdomínios que podem não ser visíveis publicamente, melhorando a segurança e gerenciamento de seus servidores web.

> [!Importante]
> A descoberta de host virtual pode gerar tráfego significativo e pode ser detectada por sistemas de detecção de intrusões (IDS) ou firewalls de aplicativos web (WAF). Tenha cuidado e obtenha a autorização adequada antes de escanear qualquer alvo.