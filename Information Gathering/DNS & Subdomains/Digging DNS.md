## Ferramentas DNS

Existem várias ferramentas especializadas para realizar consultas DNS e extrair informações valiosas:

| Ferramenta                              | Características Principais                                                                                 | Casos de Uso                                                           |
| --------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| **dig**                                 | Pesquisa versátil de DNS, suporta vários tipos de consulta e fornece saída detalhada.                      | Consultas manuais, transferências de zona, solução de problemas.       |
| **nslookup**                            | Ferramenta simples para consultas de DNS, principalmente para registros A, AAAA e MX.                      | Consultas básicas de DNS, verificações rápidas.                        |
| **host**                                | Ferramenta de pesquisa de DNS com resultados concisos.                                                     | Verificações rápidas de registros A, AAAA e MX.                        |
| **dnsenum**                             | Ferramenta automatizada de enumeração de DNS, ataques de dicionário, força bruta, transferências de zona.  | Descoberta de subdomínios e coleta de informações de DNS.              |
| **fierce**                              | Ferramenta de reconhecimento de DNS e enumeração de subdomínios com pesquisa recursiva.                    | Identificação de subdomínios e alvos potenciais.                       |
| **dnsrecon**                            | Combina várias técnicas de reconhecimento de DNS e oferece suporte a vários formatos de saída.             | Enumeração abrangente de DNS, coleta de registros DNS.                 |
| **theHarvester**                        | Ferramenta OSINT que coleta informações de diversas fontes, incluindo registros DNS (endereços de e-mail). | Coleta de endereços de e-mail, informações de funcionários.            |
| **Serviços de Pesquisa de DNS On-line** | Interfaces fáceis de usar para realizar pesquisas de DNS.                                                  | Pesquisas rápidas e fáceis, verificação de disponibilidade de domínio. |

## Usando o dig para Consultas DNS

O comando `dig` (Domain Information Groper) é um utilitário versátil para consultar servidores DNS. Aqui estão alguns comandos comuns:

|Comando|Descrição|
|---|---|
|`dig domain.com`|Pesquisa padrão para o registro A do domínio.|
|`dig domain.com A`|Recupera o endereço IPv4 (registro A) do domínio.|
|`dig domain.com AAAA`|Recupera o endereço IPv6 (registro AAAA) do domínio.|
|`dig domain.com MX`|Encontra os servidores de correio (registros MX) do domínio.|
|`dig domain.com NS`|Identifica os servidores de nomes autorizados para o domínio.|
|`dig domain.com TXT`|Recupera registros TXT associados ao domínio.|
|`dig domain.com CNAME`|Recupera o registro canônico (CNAME) do domínio.|
|`dig domain.com SOA`|Recupera o registro de início de autoridade (SOA) do domínio.|
|`dig @1.1.1.1 domain.com`|Especifica um servidor de nomes específico para consulta (1.1.1.1).|
|`dig +trace domain.com`|Mostra o caminho completo da resolução DNS.|
|`dig -x 192.168.1.1`|Pesquisa reversa no endereço IP 192.168.1.1 para encontrar o nome do host.|
|`dig +short domain.com`|Fornece uma resposta curta e concisa à consulta.|
|`dig +noall +answer domain.com`|Exibe apenas a seção de resposta da consulta.|
|`dig domain.com ANY`|Recupera todos os registros DNS disponíveis para o domínio.|

## Exemplo de Uso do dig
`dig google.com`
### Saída Explicada

```; <<>> DiG 9.18.24-0ubuntu0.22.04.1-Ubuntu <<>> google.com ;; global options: +cmd 
;; Got answer: 
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 16449 
;; flags: qr rd ad; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0 
;; WARNING: recursion requested but not available  
;; QUESTION SECTION: 
;google.com.                    IN      A  
;; ANSWER SECTION: 
google.com.             0       IN      A       142.251.47.142  
;; Query time: 0 msec ;; SERVER: 172.23.176.1#53(172.23.176.1) (UDP) ;; WHEN: Thu Jun 13 10:45:58 SAST 2024 ;; MSG SIZE  rcvd: 54
```

- **Cabeçalho**: Informações sobre a consulta, status e flags.
- **Seção de Perguntas**: Detalha a pergunta feita (registro A para google.com).
- **Seção de Respostas**: Fornece a resposta (endereço IP 142.251.47.142).
- **Rodapé**: Tempo da consulta, servidor DNS usado, carimbo de data/hora e tamanho da mensagem.

### Simplificando a Saída

Para obter apenas a resposta da consulta:

`dig +short google.com`

### Importância de Respeitar Limites

Ao realizar consultas extensivas de DNS, é crucial respeitar os limites de taxa e obter permissão, evitando bloqueios e detecção de abusos.