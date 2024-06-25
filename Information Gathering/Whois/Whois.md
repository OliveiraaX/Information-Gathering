# WHOIS: 
Um Vislumbre sobre a Propriedade de Recursos da Internet  WHOIS é um protocolo de consulta e resposta utilizado para acessar bancos de dados que armazenam informações sobre recursos registrados na Internet. Ele é amplamente associado a nomes de domínio, mas também pode fornecer detalhes sobre blocos de endereços IP e sistemas autônomos. Pense nele como uma lista telefônica da Internet, permitindo a pesquisa de quem possui ou é responsável por vários ativos online.  
## Exemplo de Consulta WHOIS  

```bash 
$ whois exemplo.com  
[...] 
Domain Name: exemplo.com 
Registry Domain ID: 2420436757_DOMAIN_COM-VRSN 
Registrar WHOIS Server: whois.registrar.amazon 
Registrar URL: https://registrar.amazon.com 
Updated Date: 2023-07-03T01:11:15Z 
Creation Date: 2019-08-05T22:43:09Z 
[...]```

## Informações Típicas em um Registro WHOIS

- **Domain Name:** O próprio nome de domínio (por exemplo, example.com)
- **Registrar:** A empresa onde o domínio foi registrado (por exemplo, GoDaddy, Namecheap)
- **Registrant Contact:** A pessoa ou organização que registrou o domínio
- **Administrative Contact:** A pessoa responsável pelo gerenciamento do domínio
- **Technical Contact:** A pessoa que trata de problemas técnicos relacionados ao domínio
- **Creation and Expiration Dates:** Datas de criação e expiração do domínio
- **Name Servers:** Servidores que traduzem o nome de domínio em um endereço IP

## História do WHOIS

A história do WHOIS está ligada à visão de Elizabeth Feinler, uma cientista da computação fundamental na formação da Internet. Nos anos 1970, Feinler e sua equipe do Network Information Center (NIC) do Stanford Research Institute criaram o diretório WHOIS para rastrear e gerenciar os recursos de rede na ARPANET, a precursora da Internet moderna.

## Importância do WHOIS para Web Reconnaissance

Os dados WHOIS são valiosos para testadores de penetração durante a fase de reconhecimento:

- **Identificação de Pessoal-Chave:** Registros WHOIS revelam nomes, e-mails e telefones de quem gerencia o domínio, úteis para ataques de engenharia social ou phishing.
- **Descoberta da Infraestrutura de Rede:** Detalhes técnicos como servidores de nomes e endereços IP ajudam a identificar possíveis pontos de entrada ou configurações incorretas.
- **Análise de Dados Históricos:** Serviços como WhoisFreaks revelam mudanças na propriedade e detalhes técnicos ao longo do tempo, úteis para entender a evolução da presença digital do alvo.