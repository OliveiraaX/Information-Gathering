# Utilizando WHOIS  
Vamos considerar três cenários para ilustrar o valor dos dados WHOIS.  
## Cenário 1: 
Investigação de Phishing  Um gateway de segurança de e-mail sinaliza um e-mail suspeito enviado a vários funcionários de uma empresa. O e-mail afirma ser do banco da empresa e incentiva os destinatários a clicar em um link para atualizar as informações de sua conta. Um analista de segurança investiga o e-mail e realiza uma pesquisa WHOIS no domínio vinculado ao e-mail.  
**O registro WHOIS revela:**  
- **Registration Date:** O domínio foi registrado há poucos dias. 
- **Registrant:** As informações do registrante ficam ocultas por trás de um serviço de privacidade. 
- **Name Servers:** Os servidores de nomes estão associados a um provedor de hospedagem à prova de balas conhecido, frequentemente usado para atividades maliciosas.  

- **Conclusão:** A data de registro recente, as informações ocultas do registrante e a hospedagem suspeita sugerem fortemente uma campanha de phishing. O analista alerta o departamento de TI da empresa para bloquear o domínio e avisa os funcionários sobre o golpe. Investigações adicionais podem revelar domínios ou infraestrutura de phishing adicionais.  

## Cenário 2: 
- Análise de Malware  Um pesquisador de segurança está analisando uma nova variedade de malware que infectou vários sistemas em uma rede. O malware se comunica com um servidor remoto para receber comandos e exfiltrar dados roubados. Para obter insights sobre a infraestrutura do agente da ameaça, o pesquisador realiza uma pesquisa WHOIS no domínio associado ao servidor de comando e controle (C2).  
- **O registro WHOIS revela:** 
- **Registrant:** O domínio é registrado para um indivíduo usando um serviço de e-mail gratuito conhecido pelo anonimato. 
- **Location:** O endereço do registrante está em um país com alta prevalência de crimes cibernéticos. 
- **Registrar:** O domínio foi registrado por meio de um registrador com histórico de políticas de abuso negligentes.  

**Conclusão:** O servidor C2 provavelmente está hospedado em um servidor comprometido ou “à prova de balas”. O pesquisador usa os dados WHOIS para identificar o provedor de hospedagem e notificá-lo sobre a atividade maliciosa.  
## Cenário 3: 
Relatório de Inteligência de Ameaças  Uma empresa de segurança cibernética rastreia as atividades de um sofisticado grupo de agentes de ameaças conhecido por ter como alvo instituições financeiras. Os analistas coletam dados WHOIS em vários domínios associados às campanhas anteriores do grupo para compilar um relatório abrangente de inteligência sobre ameaças.  
**Ao analisar os registros WHOIS, os analistas descobrem os seguintes padrões:**  
- **Registration Dates:** Os domínios foram registrados em clusters, muitas vezes pouco antes de grandes ataques. 
- **Registrants:** Os registrantes usam vários pseudônimos e identidades falsas. 
- **Name Servers:** Os domínios geralmente compartilham os mesmos servidores de nomes, sugerindo uma infraestrutura comum. 
- **Takedown History:** Muitos domínios foram removidos após ataques, indicando intervenções anteriores de aplicação da lei ou de segurança.  
**Conclusão:** Esses insights permitem que os analistas criem um perfil detalhado das táticas, técnicas e procedimentos (TTPs) do ator da ameaça. O relatório inclui indicadores de comprometimento (IOCs) baseados nos dados WHOIS, que outras organizações podem usar para detectar e bloquear ataques futuros.  ## Usando WHOIS  Antes de usar o comando `whois`, você precisará garantir que ele esteja instalado em seu sistema Linux:  

```bash sudo apt update sudo apt install whois -y```

### Exemplo de Consulta WHOIS em facebook.com

$ whois facebook.com

   Domain Name: FACEBOOK.COM
   Registry Domain ID: 2320948_DOMAIN_COM-VRSN
   Registrar WHOIS Server: whois.registrarsafe.com
   Registrar URL: http://www.registrarsafe.com
   Updated Date: 2024-04-24T19:06:12Z
   Creation Date: 1997-03-29T05:00:00Z
   Registry Expiry Date: 2033-03-30T04:00:00Z
   Registrar: RegistrarSafe, LLC
   Registrar IANA ID: 3237
   Registrar Abuse Contact Email: abusecomplaints@registrarsafe.com
   Registrar Abuse Contact Phone: +1-650-308-7004
   Domain Status: clientDeleteProhibited https://icann.org/epp#clientDeleteProhibited
   Domain Status: clientTransferProhibited https://icann.org/epp#clientTransferProhibited
   Domain Status: clientUpdateProhibited https://icann.org/epp#clientUpdateProhibited
   Domain Status: serverDeleteProhibited https://icann.org/epp#serverDeleteProhibited
   Domain Status: serverTransferProhibited https://icann.org/epp#serverTransferProhibited
   Domain Status: serverUpdateProhibited https://icann.org/epp#serverUpdateProhibited
   Name Server: A.NS.FACEBOOK.COM
   Name Server: B.NS.FACEBOOK.COM
   Name Server: C.NS.FACEBOOK.COM
   Name Server: D.NS.FACEBOOK.COM
   DNSSEC: unsigned
   URL of the ICANN Whois Inaccuracy Complaint Form: https://www.icann.org/wicf/
   Last update of whois database: 2024-06-01T11:24:10Z 
   [...]
   Registry Registrant ID:
   Registrant Name: Domain Admin
   Registrant Organization: Meta Platforms, Inc.
   [...]

**A saída WHOIS revela vários detalhes importantes:**

- **Domain Registration:**
    - **Registrar:** RegistrarSafe, LLC
    - **Creation Date:** 29/03/1997
    - **Expiry Date:** 30/03/2033
- **Domain Owner:**
    - **Registrant/Admin/Tech Organization:** Meta Platforms, Inc.
    - **Registrant/Admin/Tech Contact:** Domain Admin
- **Domain Status:**
    - clientDeleteProhibited, clientTransferProhibited, clientUpdateProhibited, serverDeleteProhibited, serverTransferProhibited, serverUpdateProhibited
- **Name Servers:**
    - A.NS.FACEBOOK.COM, B.NS.FACEBOOK.COM, C.NS.FACEBOOK.COM, D.NS.FACEBOOK.COM

**Conclusão:** O resultado WHOIS está alinhado com as expectativas de um domínio bem estabelecido e seguro de propriedade de uma grande organização como a Meta Platforms, Inc.

Embora o registro WHOIS forneça informações de contato para questões relacionadas ao domínio, ele pode não ser diretamente útil na identificação de funcionários individuais ou de vulnerabilidades específicas. Isto destaca a necessidade de combinar dados WHOIS com outras técnicas de reconhecimento para compreender de forma abrangente a pegada digital do alvo.