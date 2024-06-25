**Robots.txt é um guia de etiqueta virtual para bots da web**, indicando quais áreas de um site podem ser acessadas e quais devem ser evitadas. Semelhante a uma festa, onde certas salas são marcadas como "privadas", robots.txt orienta os bots sobre as partes do site que não devem rastrear.

#### O Que é robots.txt?

Robots.txt é um arquivo de texto simples, colocado no diretório raiz de um site (por exemplo, [www.example.com/robots.txt](http://www.example.com/robots.txt)), que segue o Padrão de Exclusão de Robôs. Este arquivo contém diretrizes que instruem os bots sobre quais partes do site podem ou não ser acessadas.

#### Funcionamento do robots.txt

As diretrizes em robots.txt normalmente têm como alvo agentes de usuário específicos (identificadores para diferentes tipos de bots). Um exemplo básico de diretiva é:

`User-agent: * Disallow: /private/`

Esta diretiva indica que todos os bots (representados pelo curinga  `"*"`) não têm permissão para acessar URLs que comecem com /private/.

#### Estrutura do robots.txt

O arquivo robots.txt é composto por registros de instruções, cada um consistindo em dois componentes principais:

- **User-agent**: Especifica a qual bot as regras se aplicam. O curinga "`*`" indica todos os bots, mas agentes específicos como "Googlebot" também podem ser direcionados.
- **Directives**: Fornecem instruções específicas para o agente de usuário identificado.

Algumas diretivas comuns incluem:

- **Disallow**: Bloqueia o acesso a caminhos ou padrões específicos.
    - Exemplo: `Disallow: /admin/` (proíbe acesso ao diretório de administração).
- **Allow**: Permite acesso a caminhos ou padrões específicos, mesmo que caiam sob uma regra Disallow mais ampla.
    - Exemplo: `Allow: /public/` (permite acesso ao diretório público).
- **Crawl-delay**: Define um atraso (em segundos) entre solicitações sucessivas do bot para evitar sobrecarregar o servidor.
    - Exemplo: `Crawl-delay: 10` (atraso de 10 segundos entre solicitações).
- **Sitemap**: Fornece o URL para um mapa do site XML para um rastreamento mais eficiente.
    - Exemplo: `Sitemap: https://www.example.com/sitemap.xml`

#### Importância de Respeitar o robots.txt

Embora não seja estritamente aplicável (bots desonestos podem ignorá-lo), a maioria dos bots legítimos respeitarão o robots.txt por várias razões:

- **Evitar Sobrecarga do Servidor**: Limitar o acesso a certas áreas pode prevenir tráfego excessivo que pode tornar os servidores lentos ou causar falhas.
- **Proteger Informações Sensíveis**: Robots.txt pode impedir que informações privadas ou confidenciais sejam indexadas.
- **Conformidade Legal e Ética**: Ignorar as diretrizes do robots.txt pode violar os termos de serviço de um site ou levar a questões legais.

#### Robots.txt no Reconhecimento da Web

Para o reconhecimento da web, robots.txt é uma fonte valiosa de inteligência:

- **Descobrindo Diretórios Ocultos**: Caminhos não permitidos geralmente apontam para áreas que o proprietário do site deseja manter fora do alcance dos rastreadores. Esses diretórios podem conter informações confidenciais, arquivos de backup, painéis administrativos ou outros recursos interessantes para um invasor.
- **Mapeamento da Estrutura do Site**: Analisando os caminhos permitidos e proibidos, é possível criar um mapa rudimentar da estrutura do site, revelando seções não vinculadas à navegação principal e potencialmente páginas ou funcionalidades ocultas.
- **Detectando Armadilhas para Rastreadores**: Alguns sites incluem diretórios "honeypot" intencionalmente no robots.txt para atrair bots maliciosos. Identificar essas armadilhas pode fornecer informações sobre as medidas de segurança do alvo.

#### Exemplo de Arquivo robots.txt

`User-agent: * 
`Disallow: /admin/ 
`Disallow: /private/ 
`Allow: /public/  
`User-agent: Googlebot Crawl-delay: 10  
`Sitemap: https://www.exemplo.com/sitemap.xml`

Este arquivo indica:
- Todos os bots não têm permissão para acessar os diretórios /admin/ e /private/.
- Todos os *bots têm permissão para acessar o diretório /public/*.
- O *Googlebot* deve esperar 10 segundos entre as solicitações.
- O mapa do site está localizado em `https://www.exemplo.com/sitemap.xml

Analisando este robots.txt, podemos inferir a existência de um painel de administração em /admin/ e conteúdo privado em /private/.