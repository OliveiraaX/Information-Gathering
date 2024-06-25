Na vasta massa da Internet, a confiança é essencial. O protocolo SSL/TLS assegura a comunicação segura entre navegadores e sites, utilizando certificados digitais para verificar a identidade dos sites. No entanto, a emissão e gestão desses certificados podem ter falhas, que podem ser exploradas por invasores. Os registros de Transparência de Certificados (CT) ajudam a mitigar esses riscos.

## O que são registros de transparência de certificados?

**Logs de Transparência de Certificados (CT)** são registros públicos e somente anexados que documentam a emissão de certificados SSL/TLS. As Autoridades Certificadoras (CAs) devem enviar novos certificados a esses logs, que estão disponíveis para inspeção pública.

### Benefícios dos logs de CT

1. **Detecção Precoce de Certificados Fraudulentos**: Monitorar logs de CT permite identificar rapidamente certificados suspeitos.
2. **Responsabilização das Autoridades Certificadoras**: Logs públicos garantem que as CAs sigam regras e padrões, tornando suas ações visíveis.
3. **Fortalecimento da Infraestrutura de Chave Pública da Web (PKI)**: Logs de CT melhoram a segurança e integridade da PKI da Web, proporcionando supervisão pública dos certificados.

### Logs de CT e Reconhecimento de Web

Os logs de CT são úteis para a enumeração de subdomínios, oferecendo uma visão histórica e abrangente dos certificados emitidos para um domínio. Diferente da força bruta, os logs de CT revelam subdomínios de forma definitiva, incluindo subdomínios antigos ou expirados que podem ser vulneráveis.

## Ferramentas para pesquisar logs de CT

### crt.sh

- **Características**: Interface web amigável, pesquisa por domínio, exibe detalhes dos certificados.
- **Casos de Uso**: Pesquisas rápidas e fáceis, identificação de subdomínios, verificação de histórico de emissão de certificados.
- **Prós**: Gratuito, fácil de usar, sem necessidade de registro.
- **Contras**: Opções limitadas de filtragem e análise.

### Censys

- **Características**: Mecanismo de busca para dispositivos conectados à Internet, filtragem avançada por domínio, IP e atributos de certificado.
- **Casos de Uso**: Análise aprofundada de certificados, identificação de configurações incorretas, descoberta de certificados e hosts relacionados.
- **Prós**: Dados abrangentes e opções de filtragem, acesso à API.
- **Contras**: Requer registro (nível gratuito disponível).

## Exemplo de pesquisa de logs de CT usando crt.sh

`$ curl -s "https://crt.sh/?q=facebook.com&output=json" | jq -r '.[]  | select(.name_value | contains("dev")) | .name_value' | sort -u `<br>    
`*.dev.facebook.com `<br>
`*.newdev.facebook.com `<br> 
`*.secure.dev.facebook.com dev.facebook.com devvm1958.ftw3.facebook.com `<br>
`facebook-amex-dev.facebook.com `<br>
`facebook-amex-sign-enc-dev.facebook.com newdev.facebook.com secure.dev.facebook.com`

### Explicação

1. **Buscar dados em JSON de crt.sh**: `curl -s "https://crt.sh/?q=facebook.com&output=json"`
2. **Filtrar resultados com jq**: `jq -r '.[] | select(.name_value | contains("dev")) | .name_value'`
3. **Classificar e remover duplicatas**: `sort -u`

Este comando busca certificados para `facebook.com`, filtra aqueles que contêm "dev" no campo `name_value` e exibe subdomínios únicos e ordenados.
