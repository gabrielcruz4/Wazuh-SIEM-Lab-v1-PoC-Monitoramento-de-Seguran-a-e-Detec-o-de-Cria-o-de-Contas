# Arquitetura do Laboratório

## Visão geral

O laboratório foi composto por duas máquinas virtuais:

1. Ubuntu Server — Wazuh Manager
2. Windows 10 — Wazuh Agent

O Dashboard do Wazuh foi utilizado para visualização e análise
dos eventos.

## Componentes

### Wazuh Manager

Sistema:
Ubuntu Server

Responsabilidade:

- receber eventos;
- processar logs;
- aplicar regras;
- gerar alertas;
- disponibilizar informações para o Dashboard.

### Wazuh Agent

Sistema:
Windows 10

Responsabilidade:

- coletar eventos do endpoint;
- monitorar o Windows Security Event Channel;
- encaminhar os eventos para o Manager.

## Fluxo

Windows 10
    ↓
Security Event Channel
    ↓
Wazuh Agent
    ↓
Wazuh Manager
    ↓
Regras / Decoders
    ↓
Wazuh Dashboard
    ↓
Analista

## Comunicação

A comunicação utilizada no laboratório envolveu as portas
1514 e 1515 do Wazuh, conforme a configuração do ambiente.

## Arquivo de configuração

O agente utilizou:

C:\Program Files (x86)\ossec-agent\ossec.conf

> O caminho acima corresponde ao ambiente utilizado durante o
> laboratório. Caminhos podem variar conforme versão/instalação.
