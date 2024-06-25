A técnica de Enumeração por Força Bruta de Subdomínios é uma abordagem poderosa para descobrir subdomínios de um domínio alvo usando listas predefinidas de possíveis nomes de subdomínios. Esse método é eficaz para identificar subdomínios válidos que podem conter informações valiosas para reconhecimento de web ou testes de segurança.

### Passos do Processo de Força Bruta de Subdomínios:

1. **Seleção da Lista de Palavras:**
    
    - A escolha da lista de palavras é crucial. Existem três tipos principais:
        - **Geral**: Contém uma ampla variedade de nomes comuns de subdomínios como `dev`, `staging`, `blog`, etc.
        - **Direcionado**: Focado em setores específicos, tecnologias ou padrões de nomenclatura relevantes para o alvo.
        - **Personalizado**: Criado com base em palavras-chave específicas ou padrões de nomenclatura conhecidos do alvo.
        
1. **Iteração e Consulta:**
    
    - Um script ou ferramenta percorre cada entrada na lista de palavras, anexando-a ao domínio principal para formar subdomínios potenciais.
    - Por exemplo, para o domínio `example.com`, se a lista incluir `dev`, `staging`, então serão gerados subdomínios como `dev.example.com`, `staging.example.com`, etc.
    
1. **Consulta DNS:**
    
    - Para cada subdomínio potencial gerado, uma consulta DNS é realizada para verificar se ele resolve para um endereço IP válido.
    - Isso geralmente é feito usando consultas de tipo de registro A ou AAAA.
    
1. **Filtragem e Validação:**
    
    - Subdomínios que resolvem com sucesso são adicionados a uma lista de subdomínios válidos.
    - Em seguida, pode-se realizar validações adicionais, como tentar acessar o subdomínio via navegador para confirmar sua funcionalidade.

### Ferramentas Comuns para Enumeração de Subdomínios por Força Bruta:

- **dnsenum**: Ferramenta abrangente escrita em Perl para enumeração de DNS, suportando força bruta de subdomínios, recuperação de registros DNS e mais.
- **fierce**: Ferramenta fácil de usar para descoberta recursiva de subdomínios, com detecção de curingas e interface amigável.
- **dnsrecon**: Ferramenta versátil que combina múltiplas técnicas de reconhecimento de DNS, oferecendo formatos de saída personalizáveis.
- **Sublist3r**: Ferramenta para enumeração de subdomínios que usa vários mecanismos de busca para ampliar a pesquisa.
- **Amass**: Ferramenta poderosa que utiliza técnicas ativas e passivas para descobrir subdomínios.

### Exemplo de Uso com dnsenum:

Aqui está um exemplo prático usando `dnsenum` para força bruta de subdomínios no domínio `exemplo.com` usando a lista de palavras `subdomains-top1million-20000.txt` do SecLists:

`dnsenum --enum exemplo.com -f /usr/share/SecLists/Discovery/DNS/subdomains-top1million-20000.txt`

Neste comando:

- `--enum exemplo.com`: Especifica o domínio alvo para enumeração.
- `-f /usr/share/SecLists/Discovery/DNS/subdomains-top1million-20000.txt`: Indica o caminho para a lista de palavras que será usada na força bruta.
- A ferramenta tentará iterativamente cada entrada na lista de palavras anexada ao domínio `exemplo.com` para descobrir subdomínios válidos.
- `-r`: esta opção permite a força bruta recursiva de subdomínio, o que significa que, se `dnsenum`encontrar um subdomínio, ele tentará enumerar os subdomínios desse subdomínio.
### Conclusão

A enumeração por força bruta de subdomínios é uma técnica essencial no arsenal de reconhecimento de web, especialmente útil para identificar recursos ocultos, ambientes de desenvolvimento, portais de login e outras informações sensíveis. É importante usar essas técnicas com responsabilidade e dentro dos limites legais e éticos, obtendo permissão adequada antes de realizar tais atividades em um domínio alvo.