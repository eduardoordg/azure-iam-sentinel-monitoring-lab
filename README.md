\# Azure IAM \& Sentinel Monitoring Lab



\## Objetivo



Este laboratório foi criado para demonstrar conhecimentos práticos em gerenciamento de identidades, auditoria e monitoramento de segurança utilizando Microsoft Azure.



O ambiente simula um cenário corporativo básico onde usuários e grupos são administrados no Microsoft Entra ID, logs são enviados para o Log Analytics Workspace e eventos são investigados com consultas KQL.



\## Tecnologias utilizadas



\* Microsoft Entra ID

\* Azure Role-Based Access Control (RBAC)

\* Log Analytics Workspace

\* Microsoft Sentinel

\* Kusto Query Language (KQL)

\* Azure Diagnostic Settings



\## Cenário do laboratório



Foi criado um ambiente fictício chamado Eduardo Cloud Lab com usuários e grupos simulando departamentos corporativos.



Usuários criados:



\* João Silva

\* Maria Souza

\* Carlos Lima



Grupos criados:



\* Financeiro

\* RH

\* TI



Também foi configurado RBAC no Azure, atribuindo a função Leitor ao grupo TI no Resource Group do laboratório.



\## Arquitetura lógica



Microsoft Entra ID

→ Usuários e grupos

→ Diagnostic Settings

→ Log Analytics Workspace

→ Microsoft Sentinel

→ Consultas KQL e investigação de eventos



\## Atividades realizadas



\* Criação de usuários no Microsoft Entra ID

\* Criação de grupos de segurança

\* Associação de usuários a grupos

\* Configuração de RBAC no Azure

\* Criação de Log Analytics Workspace

\* Habilitação do Microsoft Sentinel

\* Configuração de Diagnostic Settings para envio de logs

\* Consulta de eventos usando KQL

\* Investigação de redefinição de senha de usuário



\## Consultas KQL utilizadas



\### Consulta de eventos de login



```kusto

SigninLogs

| sort by TimeGenerated desc

| take 20

```



\### Consulta de eventos administrativos de usuário



```kusto

AuditLogs

| where OperationName contains "user"

| sort by TimeGenerated desc

```



\### Consulta de eventos relacionados a senha



```kusto

AuditLogs

| where OperationName contains "password"

| sort by TimeGenerated desc

```



\## Evidências



\### Consulta de logs de entrada



!\[SigninLogs Query](images/01-signinlogs-query.png)



\### Consulta de eventos administrativos



!\[AuditLogs User Query](images/02-auditlogs-user-query.png)



\### Detalhes do evento investigado



!\[AuditLogs Event Details](images/03-auditlogs-event-details.png)



\## Investigação realizada



Foi investigado um evento de redefinição de senha da usuária Maria Souza.



Campos analisados:



\* InitiatedBy: responsável pela ação

\* TargetResources: usuário afetado

\* Result: resultado da operação

\* ActivityDisplayName: tipo da atividade

\* ActivityDateTime: data e hora do evento



\## Resultado



O laboratório demonstrou a capacidade de configurar um fluxo básico de monitoramento de identidade no Azure, desde a geração dos eventos no Microsoft Entra ID até a investigação dos logs no Log Analytics usando KQL.



\## Aprendizados



\* Como enviar logs do Microsoft Entra ID para o Log Analytics

\* Como validar ingestão de logs

\* Como consultar SigninLogs e AuditLogs

\* Como investigar eventos administrativos

\* Como identificar ações sensíveis como redefinição de senha

\* Como relacionar IAM, RBAC, Log Analytics e Microsoft Sentinel



