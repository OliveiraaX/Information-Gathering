## O Que é DNS?

O Sistema de Nomes de Domínio (DNS) atua como um GPS da internet, traduzindo nomes de domínio legíveis (como [www.example.com](http://www.example.com)) em endereços IP numéricos (como 192.0.2.1) que os computadores usam para se comunicar. Sem DNS, navegar na internet seria como dirigir sem mapa, uma tarefa difícil e propensa a erros.

## Como o DNS Funciona

1. **Consulta DNS**: Seu computador verifica o cache local para o endereço IP do domínio. Se não encontrar, consulta um resolvedor DNS (geralmente do seu ISP).
2. **Pesquisa Recursiva**: O resolvedor consulta servidores DNS hierarquicamente: servidor raiz, servidor TLD (como .com) e servidor autoritativo.
3. **Servidor Autoritativo**: Fornece o endereço IP correspondente ao nome de domínio.
4. **Conexão**: O resolvedor retorna o endereço IP ao seu computador, que se conecta ao site.

## Arquivo Hosts

O arquivo hosts permite mapear manualmente nomes de hosts para endereços IP, substituindo o DNS. Localizado em:

- **Windows**: `C:\Windows\System32\drivers\etc\hosts`
- **Linux/MacOS**: `/etc/hosts`

| Endereço IP  | Nome do Host    |
| ------------ | --------------- |
| 127.0.0.1    | localhost       |
| 192.168.1.XX | devserver.local |

## Conceitos e Tipos de Registros DNS

|Conceito|Descrição|Exemplo|
|---|---|---|
|**Nome de Domínio**|Rótulo legível para um recurso da internet.|[www.example.com](http://www.example.com)|
|**Endereço IP**|Identificador numérico único para dispositivos na internet.|192.0.2.1|
|**Resolvedor DNS**|Servidor que traduz nomes de domínio em endereços IP.|Google DNS (8.8.8.8)|
|**Servidor Raiz**|Servidores de nível superior na hierarquia DNS.|a.root-servers.net|
|**Servidor TLD**|Responsáveis por domínios de topo (ex.: .com, .org).|Verisign para .com|
|**Servidor Autoritativo**|Possui o endereço IP real para um domínio.|ns1.example.com|

### Tipos de Registros DNS

|Tipo de Registro|Descrição|Exemplo de Zona|
|---|---|---|
|**A**|Mapeia um nome de host para seu endereço IPv4.|[www.example.com](http://www.example.com). IN A 192.0.2.1|
|**AAAA**|Mapeia um nome de host para seu endereço IPv6.|[www.example.com](http://www.example.com). IN AAAA 2001:db8:85a3::8a2e:370:7334|
|**CNAME**|Cria um alias para um hostname.|blog.example.com. IN CNAME webserver.example.net.|
|**MX**|Especifica os servidores de email do domínio.|example.com. IN MX 10 mail.example.com.|
|**NS**|Delegam uma zona DNS para um servidor autoritativo.|example.com. IN NS ns1.example.com.|
|**TXT**|Armazena informações de texto, usadas para verificação e segurança.|example.com. IN TXT "v=spf1 mx -all" (SPF record)|

## Importância do DNS para Web Recon

- **Descoberta de Ativos**: Revela subdomínios, servidores de email e outros recursos.
- **Mapeamento da Infraestrutura**: Identifica provedores de hospedagem e servidores de balanceamento de carga.
- **Monitoramento de Mudanças**: Detecta alterações na infraestrutura que podem indicar novos pontos de entrada ou vulnerabilidades.