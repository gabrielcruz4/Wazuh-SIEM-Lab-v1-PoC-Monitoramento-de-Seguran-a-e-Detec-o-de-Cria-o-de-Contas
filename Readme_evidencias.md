## Relatório de Evidência Forense - Wazuh Lab

### 1. Objetivo
Detectar e documentar a criação de uma conta de usuário com privilégio de administrador em estação Windows 11 usando o Wazuh.

### 2. Procedimento Realizado
1.  Instalação do Wazuh Agent v4.9.2 no host Windows 11 - `conf.ossec.jpeg`
2.  Execução dos comandos para criação do usuário `teste_forense` e elevação a Administrador - `criação_de_usuario.jpeg`
3.  Verificação do status do Agent no Manager - `statuswazuhagentcontrol.jpeg`
4.  Coleta dos logs de evento gerados - `Log_de_evento1.jpeg` até `Log_de_evento3.jpeg`

### 3. Ocorrência e Justificativa Técnica
Durante a prática ocorreu falha de comunicação entre o Agent e o Manager. 
O status do agente permaneceu como `Never connected` conforme evidenciado em `statuswazuhagentcontrol.jpeg` e `wazuhdashboard.jpeg`.

Causa provável: Corrupção do serviço `WazuhSvc` após tentativas de reinstalação. 
Consequência: O Agent não conseguiu enviar os alertas para o `/var/ossec/logs/alerts.json` do Manager.

### 4. Mitigação e Validação da Evidência
Mesmo com a falha de conexão, a evidência é válida pois:
O Wazuh Agent já estava instalado e monitorando o Log de Segurança do Windows por padrão.
A ação maliciosa foi registrada localmente no Windows com EventID 4720 "Uma conta de usuário foi criada" e EventID 4732 "Membro adicionado ao grupo".
Esses eventos foram coletados diretamente via `wevtutil` e anexados como `Log_de_eventoX.jpeg`.

Em ambiente de produção com o Agent `Active`, esses mesmos EventIDs seriam detectados pela regra 60103 e 60106 do Wazuh e enviados para o Dashboard.

### 5. Conclusão
A prática demonstra que mesmo com falha de comunicação, a coleta forense local é possível. 
A criação do usuário `teste_forense` foi comprovada através dos logs nativos do Windows.
