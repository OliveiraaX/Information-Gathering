
Web reconnaissance é uma fase essencial da avaliação de segurança, focada na coleta meticulosa de informações sobre um site ou aplicativo alvo. Pense nisso como uma preparação antes de uma análise mais profunda e exploração potencial, sendo uma parte crítica da fase de Information Gathering no processo de teste de penetração.

**Objetivos Principais do Reconhecimento Web:**

1. **Identificar Ativos:** Descobrir componentes publicamente acessíveis do alvo, como páginas da web, subdomínios, endereços IP e tecnologias utilizadas.
2. **Descobrir Informações Ocultas:** Localizar informações confidenciais expostas inadvertidamente, como arquivos de backup e configurações.
3. **Analisar a Superfície de Ataque:** Identificar possíveis vulnerabilidades e fraquezas na infraestrutura e configuração do alvo.
4. **Coletar Inteligência:** Obter informações para exploração adicional ou ataques de engenharia social, como detalhes de pessoal-chave e padrões de comportamento.

**Tipos de Reconhecimento:**

1. **Reconhecimento Ativo:**
    
    - Envolve interação direta com o sistema alvo para coletar informações.
    - **Técnicas:**
        - **Port Scanning:** Identificação de portas abertas e serviços.
        - **Vulnerability Scanning:** Sondagem para vulnerabilidades conhecidas.
        - **Network Mapping:** Mapeamento da topologia de rede.
        - **Banner Grabbing:** Recuperação de informações de banners de serviços.
        - **OS Fingerprinting:** Identificação do sistema operacional.
        - **Service Enumeration:** Determinação de versões específicas de serviços.
        - **Web Spidering:** Rastreamento do site para identificar páginas e diretórios.
    - **Risco de Detecção:** Alto, pois envolve interação direta que pode acionar sistemas de detecção.
    
2. **Reconhecimento Passivo:**
    - Coleta informações sem interagir diretamente com o sistema alvo.
    - **Técnicas:**
        - **Search Engine Queries:** Uso de mecanismos de pesquisa para descobrir informações.
        - **WHOIS Lookups:** Consulta a bancos de dados WHOIS para detalhes de registro de domínio.
        - **DNS Analysis:** Análise de registros DNS para identificar subdomínios e infraestrutura.
        - **Web Archive Analysis:** Exame de instantâneos históricos de sites.
        - **Social Media Analysis:** Coleta de informações de plataformas de mídia social.
        - **Code Repositories:** Análise de repositórios de código públicos para credenciais ou vulnerabilidades.
    - **Risco de Detecção:** Muito baixo, pois depende de informações publicamente acessíveis.

**Ferramentas e Técnicas Essenciais:**

- **WHOIS:** Fornece informações sobre registros de domínio, detalhes de propriedade e infraestrutura digital.
- Outras ferramentas incluem Nmap, Masscan, Nessus, OpenVAS, Traceroute, Netcat, dig, nslookup, Wayback Machine, LinkedIn, GitHub, entre outras.

A compreensão desses métodos é fundamental para uma avaliação de segurança completa, permitindo que tanto atacantes quanto defensores identifiquem e corrijam vulnerabilidades de forma eficaz.