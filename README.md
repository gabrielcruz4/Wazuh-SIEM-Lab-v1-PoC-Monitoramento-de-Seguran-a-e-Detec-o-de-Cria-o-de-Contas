# Wazuh SIEM — Windows Security Monitoring

Laboratório de SIEM utilizando **Wazuh Manager + Wazuh Agent** para monitoramento de eventos de segurança do Windows e detecção de criação de contas locais.

## Status do projeto

🟢 **V1 — Concluída**

🟡 **V2 — Planejada**

A V1 do laboratório foi implementada e validada com sucesso.

A expansão para a V2 está temporariamente pausada devido às limitações de recursos computacionais do ambiente de laboratório.

---

# V1 — Windows Security Monitoring

## Objetivo

Implementar uma arquitetura básica de SIEM capaz de coletar, processar e apresentar eventos de segurança provenientes de um endpoint Windows.

## Caso de uso

Detecção de criação de contas locais através do:

**Event ID 4720**

## Resultado

Foi validada a seguinte cadeia:

```text
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
```

Durante os testes, uma conta local foi criada em ambiente controlado e o evento correspondente foi identificado pelo Wazuh.

## Principais tecnologias

- Wazuh
- SIEM
- Windows 10
- Ubuntu Server
- Windows Security Event Channel
- MITRE ATT&CK
- Event ID 4720

## Documentação

### V1 — Concluída

[Ver documentação da V1](V1-Concluida/README.md)

### V2 — Planejada

A V2 terá como objetivo expandir o laboratório com novos mecanismos de monitoramento e detecção.

Funcionalidades planejadas:

- Sysmon;
- Process Monitoring;
- PowerShell Monitoring;
- File Integrity Monitoring;
- Authentication Monitoring;
- Regras personalizadas;
- Threat Hunting;
- Active Response.

## Observação

O projeto foi desenvolvido em ambiente virtualizado e controlado para fins educacionais.

A limitação atual de recursos computacionais levou à pausa temporária da expansão do laboratório. A V1 permanece como uma PoC funcional e documentada.
