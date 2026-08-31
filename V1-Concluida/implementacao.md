# Implementação

## 1. Wazuh Manager

Foi utilizado um Ubuntu Server como Wazuh Manager.

O Manager foi configurado para receber e processar eventos
provenientes do endpoint Windows.

## 2. Wazuh Agent

Foi utilizado um Windows 10 como endpoint monitorado.

O agente Wazuh foi instalado no Windows e configurado para
comunicação com o Manager.

## 3. Coleta do Windows Security Event Channel

O agente foi configurado para coletar o canal Security através
do seguinte bloco:

```xml
<localfile>
  <location>Security</location>
  <log_format>eventchannel</log_format>
</localfile>
