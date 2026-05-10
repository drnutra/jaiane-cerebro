---
title: Vault curado - 01-FUNIL/PT1 Boas-Vindas
publish: true
tags: [vault, curado]
---

# Vault curado - 01-FUNIL/PT1 Boas-Vindas

---
tags: [funil, parte-1]
cor: pink
lifecycle_id: 773534
tag_id: 3923048
---
# PT1 — Boas-Vindas

Primeira parte do funil. Lead crua → disparo automático.

## Sequência
1. **TEXT:** "Oi {nome}, tudo bem? Aqui é a 00-IDENTIDADE/Jaiane do Flor da Pele🩷"
2. **AUDIO:** 03-ACERVO-AUDIO/01 Boas-Vindas
3. **ASK:** "A senhora pode ficar a vontade e me responder em áudio, tá bem?"

## Regras
- Lead em PARTE 1 sem histórico → 06-WORKFLOWS/Disparo PT1 Automático (não pede confirmação — Regra 1)
- Após enviar: aguarda resposta → vai pra 01-FUNIL/PT2 Personalização
- Se silêncio: dispara 06-WORKFLOWS/Re-engager T+0 a T+24h

## Conexões
- Próxima: 01-FUNIL/PT2 Personalização
- Tag: 3923048 FUNIL-PT1 → 06-WORKFLOWS/Tag + Lifecycle
