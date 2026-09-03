# V1 — Windows Security Monitoring

## Status

🟢 **Concluída**

## Objetivo

Implementar e validar um laboratório de SIEM utilizando Wazuh Manager e Wazuh Agent para monitoramento de eventos de segurança do Windows.

## Caso de uso

Detecção da criação de contas locais através do **Windows Event ID 4720**.

## Ambiente

- **Wazuh Manager:** Ubuntu Server
- **Wazuh Agent:** Windows 10
- **Wazuh Dashboard**
- **Windows Security Event Channel**

## O que foi implementado

- Configuração do Wazuh Manager;
- Configuração do Wazuh Agent;
- Comunicação entre Agent e Manager;
- Coleta do canal Security;
- Monitoramento de eventos do Windows;
- Simulação controlada de criação de usuários;
- Detecção do Event ID 4720;
- Análise do alerta no Dashboard;
- Análise dos dados do evento;
- Troubleshooting da configuração do agente;
- Validação da detecção.

## Resultado

A cadeia de monitoramento foi validada:

```text
Windows 10
    ↓
Event ID 4720
    ↓
Wazuh Agent
    ↓
Wazuh Manager
    ↓
Regra de detecção
    ↓
Wazuh Dashboard
```

A criação de uma conta local foi detectada com sucesso pelo Wazuh.

## Documentação

- [Arquitetura](arquitetura.md)
- [Implementação](implementacao.md)
- [Detecção do Event ID 4720](deteccao-event-id-4720.md)
- [Troubleshooting](troubleshooting.md)
- [MITRE ATT&CK](mitre-attack.md)
- [Evidências](evidencias/)

## Observação

Esta versão representa uma PoC educacional.

A expansão para funcionalidades adicionais está planejada para a V2.
