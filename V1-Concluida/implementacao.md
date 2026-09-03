# Implementação

## 1. Wazuh Manager

Foi utilizado um Ubuntu Server como Wazuh Manager.

O Manager foi configurado para receber e processar eventos provenientes do endpoint Windows.

## 2. Wazuh Agent

Foi utilizado um Windows 10 como endpoint monitorado.

O agente Wazuh foi instalado no Windows e configurado para comunicação com o Manager.

## 3. Coleta do Windows Security Event Channel

O agente foi configurado para coletar o canal Security através do seguinte bloco:

```xml
<localfile>
  <location>Security</location>
  <log_format>eventchannel</log_format>
</localfile>
```

## 4. Reinicialização do Wazuh Agent

Após a alteração do arquivo `ossec.conf`, o serviço do Wazuh Agent foi reiniciado para aplicar a nova configuração.

A reinicialização foi realizada através do PowerShell executado como Administrador:

```powershell
NET STOP WazuhSvc
NET START WazuhSvc
```

## 5. Simulação controlada

Para validar a detecção, foram criadas contas locais no Windows em um ambiente de laboratório.

Foi utilizado o seguinte comando:

```cmd
net user prova_teste /add
```

Também foram utilizados outros nomes de contas durante os testes.

O objetivo foi gerar o **Event ID 4720**, correspondente à criação de uma conta de usuário no Windows.

## 6. Validação no Wazuh Dashboard

Após a criação das contas, os eventos foram analisados no Wazuh Dashboard, através da área de eventos/Threat Hunting.

Foi possível identificar as seguintes informações no evento:

- **Event ID:** 4720
- **Canal:** Security
- **Conta criada:** `prova_teste`
- **Usuário responsável:** `vboxuser`
- **Rule ID:** 60109
- **Nível do alerta:** 8
- **Decoder:** `windows_eventchannel`
- **Location:** `EventChannel`

## 7. Resultado

A detecção foi validada com sucesso.

O evento percorreu a seguinte cadeia:

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

Dessa forma, foi comprovado que o Wazuh conseguiu coletar, processar e apresentar no Dashboard o evento de criação de uma conta local no Windows.

## 8. Observação

A implementação foi realizada em um ambiente virtualizado e controlado, exclusivamente para fins de estudo e validação de técnicas de monitoramento e detecção.

A V1 deste laboratório teve como foco o monitoramento do Windows Security Event Channel e a detecção de criação de contas locais através do Event ID 4720.
