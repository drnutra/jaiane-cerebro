---
title: Vault curado - 06-WORKFLOWS/W2-CONTINUACAO-MAPA
publish: true
tags: [vault, curado]
---

# Vault curado - 06-WORKFLOWS/W2-CONTINUACAO-MAPA

---
tags: [workflow, w2, funil-ia-continuacao, master]
workflow_id: 1778320944779189
respondio_workspace: 397015
respondio_channel: 487339
status: draft
etapas: 63
limite_oficial: 100
gap: ["braip_integration", "handoff_humano", "ramo_tudo_isso_completo"]
data_mapeamento: 2026-05-09
---

# W2 — FUNIL IA CONTINUACAO (mapa master)

Status `draft`. Trigger: `Conversa Aberta + Origem=Fluxo de trabalho` (só dispara via W1 ponte).

## Estrutura

```
TRIGGER: Conversa Aberta + filtro Origem=Fluxo de trabalho
  ↓
BRANCH ramo_dor (3 saídas):
  - calor_insonia
  - humor_secura
  - tudo_isso (lead com sintomas múltiplos)
  ↓
E4 OFERTA (mesmo nos 3 ramos):
  - Imagem oferta 3 kits: W2-E4-oferta-3-kits.png
  - Texto "🔥 CONDIÇÃO ESPECIAL — CAMPANHA PROTOCOLO PRO+40 🔥"
  - Texto detalhado dos 3 protocolos com preços
  ↓
E5 ÁUDIO MODALIDADE PAGAMENTO:
  - Áudio: W2-E5-pedido-modalidade-pix-cod.mp3
  - Texto explicando 2 formas (antecipado vs entrega)
  - AskQuestion 3 botões:
      👑 KIT 12 MESES (12m_premium)
      ⭐ KIT 8 MESES  (8m_completo)
      💗 KIT 5 MESES  (5m_inicial)
  - Tag: protocolo_escolhido
  - Custom field: protocolo_escolhido = 12m_premium | 8m_completo | 5m_inicial
  - Custom field: modalidade_pagamento = antecipado | entrega
  ↓
E6 PEDIDO DE DADOS:
  - Áudio: W2-E6-pedido-cep-dados.mp3
  - Texto "🎉 Parabéns pela decisão... informações pra inserir seu pedido"
  ↓
[GAP — em construção]:
  - Integração Braip (status agendou/tracking/pago/devolvido)
  - Handoff humano (Raíla/Wilane/Geane/Vitória)
  - Ramo tudo_isso completo
```

## Catálogo de protocolos (canônico 2026-05-09)

| Kit | Conteúdo | Preço à vista | 12x cartão |
|---|---|---|---|
| 👑 12M Premium  | 6 cápsulas + 4 gotas + 2 géis = 12 potes | R$ 767 | 12x R$ 78,90 |
| ⭐ 8M Completo  | 4 cápsulas + 3 gotas + 1 gel = 8 potes   | R$ 627 | 12x R$ 64,50 |
| 💗 5M Inicial   | 3 cápsulas + 2 gotas = 5 potes            | R$ 447 | 12x R$ 45,99 |

## Tags geradas
- `protocolo_escolhido` (depois do AskQuestion)

## Custom fields setados
- `protocolo_escolhido` = `12m_premium` | `8m_completo` | `5m_inicial`
- `modalidade_pagamento` = `antecipado` | `entrega`

## Assets referenciados
| Categoria | Arquivos |
|---|---|
| Áudios (2) | W2-E5-pedido-modalidade-pix-cod / W2-E6-pedido-cep-dados |
| Imagens (1) | W2-E4-oferta-3-kits |

## GAPs a fechar (próximas ações)
1. **Braip webhooks:**
   - status 11 (AGENDOU) → tag AGENDOU + lifecycle AGENDADO + CAPI InitiateCheckout
   - status 13 (PAGO) → tag PAGOU + lifecycle PAGO + CAPI Purchase
   - status devolvido → cobradora (Rayane / Maria) + CAPI Frustrado
   - tracking → custom field codigo_de_rastreio + link_do_rastreio + msg cliente
2. **Handoff humano:** assign pra vendedora baseada em hot_score / objeção / risco
3. **Ramo tudo_isso:** copy + áudios específicos (lead com sintomas múltiplos)
