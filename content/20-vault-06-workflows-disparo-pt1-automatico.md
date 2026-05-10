---
title: Vault curado - 06-WORKFLOWS/Disparo PT1 Automático
publish: true
tags: [vault, curado]
---

# Vault curado - 06-WORKFLOWS/Disparo PT1 Automático

---
tags: [workflow, pt1, automatico]
---
# Workflow: Disparo PT1 Automático

Regra 1 aplicada.

## Trigger
Lead novo entra no 07-INTEGRACOES/respond.io space 413594, lifecycle PARTE 1, sem histórico, mensagem padrão de abertura.

## Ação
Disparo IMEDIATO sem pedir confirmação ao Diego:
1. TEXT: "Oi {nome}, tudo bem? Aqui é a Jaiane do Flor da Pele🩷"
2. AUDIO: 03-ACERVO-AUDIO/01 Boas-Vindas
3. ASK: "A senhora pode ficar a vontade e me responder em áudio, tá bem?"
4. Apply tag `3923048 FUNIL-PT1` + lifecycle `773534 PARTE 1` (06-WORKFLOWS/Tag + Lifecycle)

## Exceção (não dispara automático)
- Re-engager (já entrou antes)
- Objeção atípica
- Lifecycle ≠ PARTE 1
- Notas de pt3/pt4 (vendedora humana já trabalhou)
