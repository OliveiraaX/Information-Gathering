### O que é uma Transferência de Zona

Uma transferência de zona DNS é um processo que envolve a cópia completa de todos os registros DNS dentro de uma zona (domínio e seus subdomínios) de um servidor de nomes para outro. Esse mecanismo é crucial para a manutenção da consistência e redundância nos servidores DNS. No entanto, se não estiver bem configurado, pode expor informações sensíveis inadvertidamente.

### Processo de Transferência de Zona

1. **Zone Transfer Request (AXFR):** O servidor DNS secundário envia uma solicitação de transferência de zona ao servidor primário usando o tipo AXFR (Full Zone Transfer).
    
2. **SOA Record Transfer:** O servidor primário responde enviando seu registro de início de autoridade (SOA), que contém informações importantes sobre a zona, incluindo seu número de série.
    
3. **DNS Records Transmission:** O servidor primário transfere todos os registros DNS da zona para o servidor secundário, incluindo registros A, AAAA, MX, CNAME, NS e outros.
    
4. **Zone Transfer Complete:** O servidor primário sinaliza o fim da transferência após enviar todos os registros DNS.
    
5. **Acknowledgement (ACK):** O servidor secundário confirma o recebimento e processamento bem-sucedido dos dados da zona.
    

### Vulnerabilidade de Transferência de Zona

As transferências de zona são essenciais para o gerenciamento do DNS, mas um servidor mal configurado pode transformar esse processo em uma vulnerabilidade significativa. No início da internet, permitir que qualquer cliente solicitasse uma transferência de zona era comum, mas essa prática expunha muitas informações confidenciais. Um atacante pode usar essas informações para mapear a infraestrutura DNS do alvo, identificando subdomínios ocultos, endereços IP e registros de servidores de nomes.

### Exploração de Transferências de Zona

Você pode utilizar o comando `dig` para solicitar uma transferência de zona:

`dig axfr @nsztm1.digi.ninja zonetransfer.me`

Este comando instrui o `dig` a solicitar uma transferência completa de zona (AXFR) do servidor DNS responsável pelo domínio `zonetransfer.me`. Se o servidor estiver configurado incorretamente e permitir a transferência, você receberá uma lista completa de registros DNS do domínio.

### Exemplo de Transferência de Zona com o `dig`

|Registro|TTL|Tipo|Valor|
|---|---|---|---|
|zonetransfer.me.|7200|SOA|nsztm1.digi.ninja. robin.digi.ninja. 2019100801 172800 900 1209600 3600|
|zonetransfer.me.|300|HINFO|"Casio fx-700G" "Windows XP"|
|zonetransfer.me.|301|TXT|"google-site-verification=tyP28J7JAUHA9fw2sHXMgcCC0I6XBmmoVi04VlMewxA"|
|zonetransfer.me.|7200|MX|0 ASPMX.L.GOOGLE.COM.|
|zonetransfer.me.|7200|A|5.196.105.14|
|zonetransfer.me.|7200|NS|nsztm1.digi.ninja.|
|zonetransfer.me.|7200|NS|nsztm2.digi.ninja.|
|_acme-challenge.zonetransfer.me.|301|TXT|"6Oa05hbUJ9xSsvYy7pApQvwCUSSGgxvrbdizjePEsZI"|
|_sip._tcp.zonetransfer.me.|14000|SRV|0 0 5060 [www.zonetransfer.me](http://www.zonetransfer.me).|
|14.105.196.5.IN-ADDR.ARPA.zonetransfer.me.|7200|PTR|[www.zonetransfer.me](http://www.zonetransfer.me).|
|asfdbauthdns.zonetransfer.me.|7900|AFSDB|1 asfdbbox.zonetransfer.me.|
|asfdbbox.zonetransfer.me.|7200|A|127.0.0.1|
|asfdbvolume.zonetransfer.me.|7800|AFSDB|1 asfdbbox.zonetransfer.me.|
|canberra-office.zonetransfer.me.|7200|A|202.14.81.230|)`

`zonetransfer.me` é um serviço configurado especificamente para demonstrar os riscos das transferências de zona, permitindo que o comando `dig` retorne o registro completo da zona.

### Mitigação

Felizmente, a maioria dos administradores de servidores DNS modernos configuram os servidores para permitir transferências de zona apenas para servidores secundários confiáveis. No entanto, erros humanos ou práticas desatualizadas ainda podem causar configurações incorretas. É crucial que administradores de sistemas verifiquem regularmente suas configurações de DNS para garantir que as transferências de zona estejam adequadamente protegidas.