
# Troubleshooting

## Problema encontrado

Durante os testes iniciais, os eventos de criação de usuários não apareciam no Wazuh Dashboard.

O Wazuh Agent aparecia como ativo, porém o Event ID 4720 não era apresentado na área de eventos.

## Investigação

Foi analisado o arquivo:

```text
C:\Program Files (x86)\ossec-agent\ossec.conf
```

No bloco responsável pela coleta do canal Security existia uma consulta `<query>` utilizada para filtrar eventos.

Esse filtro restringia a coleta necessária para o caso de uso testado.

## Situação inicial

```text
Windows
    ↓
Event ID 4720
    ↓
Wazuh Agent
    ↓
Filtro no ossec.conf
    ↓
Evento não aparecia no Dashboard
```

## Solução

O bloco de coleta foi simplificado para:

```xml
<localfile>
  <location>Security</location>
  <log_format>eventchannel</log_format>
</localfile>
```

O filtro `<query>` foi removido da configuração utilizada para o teste.

Após a alteração, o serviço do Wazuh Agent foi reiniciado.

## Reinicialização

Através do PowerShell executado como Administrador:

```powershell
NET STOP WazuhSvc
NET START WazuhSvc
```

## Resultado

Após a correção, novos eventos de criação de contas passaram a aparecer no Wazuh Dashboard.

Durante a validação, o gráfico de eventos apresentou novos registros após os testes.

## Aprendizado

O principal aprendizado foi que um agente aparecer como ativo não significa necessariamente que toda a telemetria necessária esteja sendo coletada.

A investigação de uma detecção deve considerar toda a cadeia:

```text
Endpoint
    ↓
Agent
    ↓
Configuração
    ↓
Manager
    ↓
Decoder
    ↓
Rule
    ↓
Alert
    ↓
Dashboard
```
