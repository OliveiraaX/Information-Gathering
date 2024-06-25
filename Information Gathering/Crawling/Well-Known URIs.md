#### O Que é o .well-known?

O .well-known é um padrão definido pela RFC 8615 que estabelece um diretório padronizado dentro do domínio raiz de um site. Este diretório, acessível através do caminho `/.well-known/` em um servidor web, centraliza metadados importantes do site, incluindo arquivos de configuração e informações sobre serviços, protocolos e mecanismos de segurança.

#### Benefícios do .well-known

Este padrão facilita a descoberta e o acesso a dados cruciais, permitindo que navegadores, aplicativos e ferramentas de segurança localizem automaticamente arquivos de configuração. Por exemplo, para acessar a política de segurança de um site, um cliente solicitaria a URL `https://exemplo.com/.well-known/security.txt`.

#### Registro de URIs pelo IANA

A *Internet Assigned Numbers Authority* (IANA) mantém um registro de URIs .well-known, cada um servindo a uma finalidade específica, conforme definido por diversas especificações e padrões. Alguns exemplos notáveis incluem:

|Sufixo URI|Descrição|Status|Referência|
|---|---|---|---|
|security.txt|Contém informações de contato para relatórios de vulnerabilidades.|Permanente|RFC 9116|
|/change-password|Fornece um URL padrão para direcionar usuários a uma página de alteração de senha.|Provisório|[Change Password URL](https://w3c.github.io/webappsec-change-password-url/#the-change-password-well-known-uri)|
|openid-configuration|Detalhes de configuração do OpenID Connect, uma camada de identidade sobre o protocolo OAuth 2.0.|Permanente|[OpenID Connect Discovery](http://openid.net/specs/openid-connect-discovery-1_0.html)|
|assetlinks.json|Verifica a propriedade de ativos digitais associados a um domínio.|Permanente|[Digital Asset Links](https://github.com/google/digitalassetlinks/blob/master/well-known/specification.md)|
|mta-sts.txt|Especifica a política para SMTP MTA Strict Transport Security (MTA-STS) para segurança de email.|Permanente|RFC 8461|

#### .well-known no Reconhecimento da Web

No contexto de reconhecimento da web, os URIs .well-known são valiosos para descobrir endpoints e detalhes de configuração que podem ser úteis em testes de penetração. Um exemplo útil é o URI `openid-configuration`.

#### OpenID-Configuration

O URI `openid-configuration` faz parte do protocolo OpenID Connect Discovery. Um aplicativo cliente pode recuperar a configuração do provedor OpenID Connect acessando `https://exemplo.com/.well-known/openid-configuration`. Este endpoint retorna um documento JSON com metadados sobre os endpoints do provedor, métodos de autenticação, emissão de token, e mais:

`{"issuer": "https://exemplo.com",   "authorization_endpoint": "https://exemplo.com/oauth2/authorize",   
`"token_endpoint": "https://exemplo.com/oauth2/token",   "userinfo_endpoint": "https://exemplo.com/oauth2/userinfo",  
`"jwks_uri": "https://exemplo.com/oauth2/jwks",   "response_types_supported": ["code", "token", "id_token"],   "subject_types_supported": ["public"],   "id_token_signing_alg_values_supported": ["RS256"],   "scopes_supported": ["openid", "profile", "email"] }`

##### Oportunidades de Exploração:

- **Descoberta de Endpoints**:
    
    - `authorization_endpoint`: URL para solicitações de autorização de usuário.
    - `token_endpoint`: URL onde os tokens são emitidos.
    - `userinfo_endpoint`: URL que fornece informações do usuário.
    - `jwks_uri`: Detalhes sobre chaves criptográficas usadas pelo servidor.
- **Escopos e Tipos de Resposta Suportados**: Ajuda a mapear funcionalidades e limitações do OpenID Connect.
    
- **Detalhes de Algoritmo**: Informações sobre algoritmos de assinatura suportados, importantes para entender as medidas de segurança.
    

Explorar o registro da IANA e experimentar os vários URIs .well-known é uma abordagem valiosa para descobrir oportunidades adicionais de reconhecimento da web. Esses URIs padronizados fornecem acesso estruturado a metadados críticos e detalhes de configuração, permitindo que os profissionais de segurança mapeiem de forma abrangente o cenário de segurança de um site.