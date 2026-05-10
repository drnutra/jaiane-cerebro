---
title: Vault curado - 06-WORKFLOWS/PONTE-W1-W2
publish: true
tags: [vault, curado]
---

# Vault curado - 06-WORKFLOWS/PONTE-W1-W2

---
tags: [workflow, ponte, integracao, w1-w2]
data_mapeamento: 2026-05-09
---

# Ponte W1 → W2

## Como funciona
W1 termina no E3 com tag `passou_parte2` e dispara `triggerWorkflow` apontando pra W2.
W2 tem trigger `Conversa Aberta + filtro Origem=Fluxo de trabalho` — só executa quando vem de outro workflow (W1).

## Custom field bridge
`ramo_dor` é setado em W1 antes do `triggerWorkflow`. W2 abre BRANCH baseado nele.

| Tag W1 | ramo_dor (custom field) | BRANCH W2 |
|---|---|---|
| `dor_vaso` (calor + insônia) | `calor_insonia` | calor_insonia |
| `dor_humor` (nervosa + ansiosa) | `humor_secura` | humor_secura |
| `dor_intim` (secura + sem desejo) | `humor_secura` ou `tudo_isso` | humor_secura ou tudo_isso |
| múltiplas | `tudo_isso` | tudo_isso |

## Riscos / brechas
1. Se `ramo_dor` não setar, W2 BRANCH não roteia → lead trava.
2. Se W1 deletar tag `passou_parte2` por engano, W2 não dispara mesmo com trigger correto.
3. Se W1 reativar enquanto está em 104/100, pode quebrar publish.

## Recomendação
Quebrar W1 em 4 sub-workflows:
- W1A — Boas-Vindas + E2 Pergunta de Dor (~25 etapas)
- W1B-VASO (ramo VASO completo) (~25 etapas)
- W1B-HUMOR (ramo HUMOR completo) (~25 etapas)
- W1B-INTIM (ramo INTIM completo) (~25 etapas)
- W1C — E3 Pós-Provas + ponte W2 (~10 etapas)

Resolve gargalo 104/100 e mantém comportamento idêntico.
