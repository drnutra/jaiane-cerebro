---
title: Vault curado - 06-WORKFLOWS/W1-FUNIL-IA-MAPA
publish: true
tags: [vault, curado]
---

# Vault curado - 06-WORKFLOWS/W1-FUNIL-IA-MAPA

---
tags: [workflow, w1, funil-ia, master]
workflow_id: 1777912630463096
respondio_workspace: 397015
respondio_channel: 487339
status: stopped
etapas: 104
limite_oficial: 100
gargalo: true
data_mapeamento: 2026-05-09
---

# W1 — FUNIL IA (mapa master)

⚠️ **GARGALO:** 104/100 etapas — acima do limite oficial respond.io. Status `stopped`. Pode falhar publish/comportamento imprevisível. **Solução:** quebrar em sub-workflows.

## Estrutura

```
TRIGGER: CTWA WhatsApp 487339
  ↓
E1 BOAS-VINDAS:
  - Texto saudação ("Oi {{firstname}} 🩷 Aqui é a Jaiane...")
  - Áudio: W1-E1-01-boas-vindas-jaiane.mp3
  - Texto explicação inicial
  - Tag: in_funil
  ↓
E2 PERGUNTA DE DOR (3 botões):
  🔥 Calor e insônia       → ramo VASO
  🤒 Nervosa e ansiosa     → ramo HUMOR
  💔 Secura sem desejo     → ramo INTIM
  ↓
E2.{RAMO} (mesmo padrão pros 3):
  - Imagem confirmação:    W1-E2-{RAMO}-confirmacao.png
  - Texto Cláudia Raia / Adriane Galisteu
  - Áudio reflexivo:       W1-E2-{RAMO}-01-reflexivo.mp3
  - Áudio mecanismo:       W1-E2-{RAMO}-02-mecanismo.mp3
  - Vídeo prova social:    W1-E2-prova-social-mulher-relato.mp4 (compartilhado)
  - Vídeo fechamento+CTA:  W1-E2-fechamento-cta-produto.mp4   (compartilhado)
  - Tag: dor_vaso | dor_humor | dor_intim
  - Custom field: ramo_dor = calor_insonia | humor_secura | tudo_isso
  ↓
E3 PÓS-PROVAS:
  - Tag: passou_parte2
  - Áudio fechamento: W1-E3-fechamento-pos-provas.mp3 (compartilhado)
  - Texto Garantia DR NUTRA
  ↓
PONTE: triggerWorkflow → W2
```

## Recovery paralelo
3 askQuestions com timer + closeConversation — pra leads que sumiram em E2 ou pós-provas.

## Tags geradas
- `in_funil` (entrada)
- `dor_vaso` | `dor_humor` | `dor_intim` (escolha botão)
- `passou_parte2` (chegou no E3 — bridge pra W2)

## Custom fields setados
- `ramo_dor` = `calor_insonia` | `humor_secura` | `tudo_isso`

## Assets referenciados
| Categoria | Arquivos |
|---|---|
| Áudios (8) | W1-E1-01-boas-vindas / W1-E2-VASO/HUMOR/INTIM-01-reflexivo + 02-mecanismo / W1-E3-fechamento-pos-provas |
| Imagens (3) | W1-E2-VASO/HUMOR/INTIM-confirmacao |
| Vídeos (2) | W1-E2-prova-social-mulher-relato / W1-E2-fechamento-cta-produto |

## Próximas ações
- Receber pasta `FUNIL_DR_NUTRA_ORGANIZADO/` e indexar áudios+imagens+vídeos no acervo
- Quebrar em sub-workflows pra resolver 104/100
- Conectar n8n master pra resposta inteligente complementar (não substituir o W1 publicado)
