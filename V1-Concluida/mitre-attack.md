# MITRE ATT&CK

## Contexto

Durante o laboratório, o alerta observado foi associado pelo ambiente ao contexto:

**T1098 — Account Manipulation**

**Tática:** Persistence

Entretanto, durante a revisão da documentação, foi identificado que existe uma técnica mais específica para o cenário testado.

## Mapeamento recomendado

### T1136.001 — Create Account: Local Account

**Tática:** Persistence

O cenário realizado no laboratório consiste na criação de uma conta local utilizando:

```cmd
net user prova_teste /add
```

Portanto, para a documentação do cenário testado, o mapeamento mais específico é:

```text
Persistence
    ↓
T1136.001 — Create Account: Local Account
```

## Relação com T1098

A técnica **T1098 — Account Manipulation** pode ser relevante em cenários nos quais uma conta existente é modificada.

Uma futura expansão do laboratório poderá investigar técnicas relacionadas à manipulação de grupos e privilégios de contas.

## Observação

O mapeamento apresentado pelo ambiente durante a realização do laboratório foi mantido como parte do registro histórico.

A técnica T1136.001 foi adicionada à documentação por representar de forma mais específica o cenário de criação de uma conta local utilizado neste laboratório.
