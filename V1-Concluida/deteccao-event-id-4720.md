# Detecção — Windows Event ID 4720

## Objetivo

Detectar a criação de uma nova conta de usuário local em um endpoint Windows.

## Evento monitorado

**Event ID:** 4720

**Canal:** Security

O Event ID 4720 representa a criação de uma conta de usuário no Windows.

## Simulação controlada

Foi utilizado o seguinte comando em ambiente de laboratório:

```cmd
net user prova_teste /add
```

Também foram utilizados outros nomes de contas durante os testes.

## Dados observados

No evento analisado foram identificados:

```text
Event ID: 4720
Channel: Security
Target User Name: prova_teste
Subject User Name: vboxuser
Rule ID: 60109
Rule Level: 8
Decoder: windows_eventchannel
Location: EventChannel
```

## Interpretação

**Target User Name**

Identifica a conta criada no evento.

**Subject User Name**

Identifica o usuário associado à ação registrada pelo Windows.

**Rule ID**

Identifica a regra do Wazuh responsável pelo alerta.

**Rule Level**

Indica o nível de severidade atribuído ao alerta.

**Decoder**

Indica o decoder utilizado para interpretar o evento do Windows.

## Cadeia de detecção

```text
Criação da conta
      ↓
Windows Event ID 4720
      ↓
Wazuh Agent
      ↓
Wazuh Manager
      ↓
Rule 60109
      ↓
Alert Level 8
      ↓
Wazuh Dashboard
```

## Resultado

A criação da conta foi detectada com sucesso pelo Wazuh e apresentada no Dashboard para análise.
