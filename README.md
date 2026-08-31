# Wazuh SIEM — Windows Security Monitoring

Laboratório de SIEM utilizando Wazuh Manager + Wazuh Agent para
monitoramento de eventos de segurança do Windows e detecção de
criação de contas locais.

## Status do projeto

🟢 V1 — Concluída  
🟡 V2 — Planejada

O ambiente base foi implementado e validado na V1.

A expansão para a V2 está temporariamente pausada devido às
limitações de recursos computacionais do ambiente de laboratório.

---

# V1 — Windows Security Monitoring

## Objetivo

Implementar uma arquitetura básica de SIEM capaz de coletar,
processar e apresentar eventos de segurança provenientes de
um endpoint Windows.

## Ambiente

- Wazuh Manager — Ubuntu Server
- Wazuh Agent — Windows 10
- Wazuh Dashboard
- Windows Security Event Channel

## Caso de uso

Detecção de criação de contas locais através do:

Event ID 4720

## Fluxo

Windows 10
↓
Security Event Channel
↓
Wazuh Agent
↓
Wazuh Manager
↓
Regra de detecção
↓
Wazuh Dashboard
↓
Análise

## Validação

Foi utilizado o seguinte comando em ambiente controlado:

net user prova_teste /add

O Windows gerou o Event ID 4720 e o evento foi posteriormente
recebido e apresentado pelo Wazuh.

## Resultado

A detecção foi validada com sucesso.

Foram identificados:

- Event ID 4720
- Canal Security
- Conta criada
- Usuário responsável pela ação
- Rule ID 60109
- Level 8
- Decoder windows_eventchannel

## Troubleshooting

Durante a implementação, o agente estava ativo, porém o
Event ID 4720 não aparecia no Dashboard.

A investigação identificou uma consulta `<query>` no
`ossec.conf` que restringia a coleta do canal Security.

A configuração foi simplificada e o agente reiniciado.

Após a correção, os eventos passaram a ser recebidos normalmente.

---

# V2 — Planejada

A segunda versão pretende transformar o laboratório em um
ambiente SOC mais completo.

## Planejamento

### 1. Sysmon
⬜ Instalação e configuração

### 2. Process Monitoring
⬜ Detecção de criação de processos

### 3. PowerShell
⬜ Monitoramento de execução
⬜ Detecções relacionadas

### 4. FIM
⬜ File Integrity Monitoring
⬜ Alteração de arquivos
⬜ Criação de arquivos

### 5. Authentication Monitoring
⬜ Event ID 4624
⬜ Event ID 4625
⬜ Event ID 4740

### 6. Custom Rules
⬜ Criação de regras próprias
⬜ Aumento de severidade
⬜ Correlação de eventos

### 7. MITRE ATT&CK
⬜ Expansão dos casos de uso
⬜ T1136.001
⬜ T1098.007
⬜ Outras técnicas

### 8. Threat Hunting
⬜ Criação de hipóteses
⬜ Investigação de eventos
⬜ Construção de timelines

### 9. Active Response
⬜ Resposta automática
⬜ Bloqueio de indicadores
⬜ Testes controlados

---

# Roadmap

V1
├── Wazuh Manager
├── Windows Agent
├── Security Event Channel
├── Event ID 4720
├── Dashboard
└── Troubleshooting
        ↓
V2
├── Sysmon
├── Process Monitoring
├── FIM
├── Authentication
├── Custom Rules
├── MITRE ATT&CK
├── Threat Hunting
└── Active Response
