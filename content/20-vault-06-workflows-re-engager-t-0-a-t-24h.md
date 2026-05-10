---
title: Vault curado - 06-WORKFLOWS/Re-engager T+0 a T+24h
publish: true
tags: [vault, curado]
---

# Vault curado - 06-WORKFLOWS/Re-engager T+0 a T+24h

---
tags: [workflow, re-engager, cadencia]
---
# Workflow: Re-engager T+0 a T+24h

Regra 3: não deixar esfriar.

## Cadência
| Trigger | Ação |
|---|---|
| **T+0** | 1ª tentativa após silêncio inicial |
| **T+15min** | 2ª tentativa |
| **T+1h** | 3ª — peso médio |
| **T+4h** | 4ª — escalando |
| **T+24h** | última antes de 01-FUNIL/CANCELADO |

## Tom
Peso, não bonzinho. Cada gatilho mais firme que o anterior.

## Re-engager especial
Lead que JÁ entrou antes, sumiu, voltou → texto de peso (Regra 2):
"Você entrou em [mês], te mandei msg, sumiu, agora tô parando pra te atender — me responde X, Y ou Z."
