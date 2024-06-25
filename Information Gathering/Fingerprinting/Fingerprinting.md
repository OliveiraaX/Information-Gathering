A impressão digital foca na identificação única de tecnologias que alimentam sites e aplicativos web. Assim como uma impressão digital identifica exclusivamente uma pessoa, as assinaturas digitais de servidores web, sistemas operacionais e softwares revelam detalhes críticos da infraestrutura, ajudando invasores a personalizar ataques e explorar vulnerabilidades específicas.

### Por que a impressão digital é crucial?

1. **Ataques Direcionados**: Conhecendo as tecnologias específicas, invasores podem focar em explorações que afetam sistemas identificados, aumentando as chances de sucesso.
    
2. **Identificação de Malconfigurações**: Revela software desatualizado, configurações padrão e outras fraquezas que podem não ser visíveis de outras maneiras.
    
3. **Priorização de Alvos**: Ajuda a identificar sistemas mais vulneráveis ou com informações valiosas, priorizando esforços de ataque.
    
4. **Construção de um Perfil Abrangente**: Combina dados de impressão digital com outras informações para entender a postura geral de segurança de um alvo.
    

### Técnicas de Impressão Digital

- **Captura de Banner**: Analisa banners de servidores web para revelar software e versões.
    
- **Análise de Cabeçalhos HTTP**: Informações como `Server` revelam o software do servidor; `X-Powered-By` indica tecnologias adicionais.
    
- **Sondagem por Respostas Específicas**: Solicitações elaboradas podem gerar respostas que revelam tecnologias ou versões específicas de software.
    
- **Análise de Conteúdo de Página**: Estrutura, scripts e elementos de uma página web podem indicar tecnologias subjacentes, como o cabeçalho de direitos autorais.
    
### Ferramentas de Impressão Digital

- **Wappalyzer**: Extensão e serviço online que identifica tecnologias web como CMSs, estruturas e ferramentas analíticas.
    
- **BuiltWith**: Cria perfis detalhados de tecnologia web, oferecendo relatórios sobre a pilha de tecnologia de um site.
    
- **WhatWeb**: Ferramenta de linha de comando para impressão digital de sites, usando um vasto banco de dados de assinaturas.
    
- **Nmap**: Scanner de rede que realiza impressões digitais de serviço e sistema operacional, útil com scripts para reconhecimento especializado.
    
- **Netcraft**: Oferece serviços de segurança na web, incluindo impressão digital de sites e relatórios detalhados de tecnologia e segurança.
    
- **wafw00f**: Identifica Web Application Firewalls (WAFs) para entender se estão presentes e suas configurações.
    

Para realizar a identificação detalhada do exemplo.com, vamos utilizar técnicas de fingerprinting tanto manualmente quanto por meio de ferramentas automatizadas.

### Captura de Banner

**Passo 1: Captura inicial do Banner** Começamos obtendo os cabeçalhos HTTP do inlanefreight.com para identificar o software do servidor e possíveis detalhes de configuração.

`$ curl -I inlanefreight.com`

**Saída:**

`HTTP/1.1 301 Moved Permanently 
`Date: Sex, 31 Mai 2024 12:07:44 GMT 
`Server: Apache/2.4.41 (Ubuntu) 
`Location: https://exemplo.com/ 
`Content-Type: text/html; charset=iso-8859-1`

- **Software do Servidor:** Apache/2.4.41 (Ubuntu)
- **Informações Adicionais:** O servidor está configurado para redirecionar tráfego HTTP para HTTPS.

**Passo 2: Seguir o Redirecionamento**

Em seguida, seguimos o redirecionamento para HTTPS para obter mais informações:

`$ curl -I https://inlanefreight.com`

**Saída:**

```HTTP/1.1 301 Moved Permanently 
Date: Sex, 31 Mai 2024 12:12:12 GMT 
Server: Apache/2.4.41 (Ubuntu) 
X-Redirect-By: WordPress 
Location: https://www.exemplo.com/ 
Content-Type: text/html; charset=UTF-8
```

- **Software do Servidor:** Apache/2.4.41 (Ubuntu)
- **X-Redirect-By:** WordPress

Este redirecionamento indica que o WordPress está gerenciando o redirecionamento para [https://www.exemplo.com/](https://www.inlanefreight.com/).

### Detecção de Firewall de Aplicação Web (WAF)

Para determinar se inlanefreight.com possui um WAF (Firewall de Aplicação Web) e identificar qual poderia ser, utilizamos a ferramenta wafw00f.

`$ wafw00f inlanefreight.com`

**Saída:**

```
[*] Checking https://exemplo.com 
[+] The site https://exemplo.com is behind Wordfence (Defiant) WAF. 
[~] Number of requests: 2
```

- **WAF Detectado:** O site está protegido pelo Wordfence WAF, desenvolvido pela Defiant.

### Utilização do Nikto

O Nikto é uma ferramenta poderosa de scanner de servidor web que também realiza identificação de software. Vamos usar o Nikto para obter mais informações sobre inlanefreight.com.

`$ nikto -h exemplo.com -Tuning b`

**Saída Resumida:**

- **IPs Encontrados:** 134.209.24.248, 2a03:b0c0:1:e0::32c
- **Tecnologia do Servidor:** Apache/2.4.41 (Ubuntu)
- **Presença do WordPress:** Instalação do WordPress identificada, incluindo a página de login (/wp-login.php).
- **Cabeçalhos e Configurações:** Alguns cabeçalhos estão ausentes ou podem ser configurados de maneira insegura, como *Strict-Transport-Security não definido e X-Content-Type-Options não definido.*
- **Arquivos e Diretórios:** Alguns arquivos padrão do WordPress foram identificados, como license.txt e wp-login.php.

Essas informações são cruciais para entender a infraestrutura digital do exemplo.com, identificando potenciais vulnerabilidades e ajudando na preparação de testes de segurança adicionais, se necessário.
### Exemplo Prático

Para o domínio `exemplo.com`, a captura de banner revelou que o site roda Apache/2.4.41 (Ubuntu), e a presença do WordPress foi identificada através do cabeçalho `X-Redirect-By`. A ferramenta `wafw00f` confirmou que o site é protegido pelo Wordfence WAF. A utilização do *Nikto* proporcionou insights adicionais sobre o site, incluindo a presença de IPs, informações sobre o servidor Apache desatualizado e a existência de uma instalação WordPress com suas vulnerabilidades potenciais.