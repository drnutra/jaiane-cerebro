---
title: Vault curado - 07-INTEGRACOES/Braip
publish: true
tags: [vault, curado]
---

# Vault curado - 07-INTEGRACOES/Braip

---
tags: [integracao, pagamento, braip]
---
# Braip

Plataforma de venda/checkout COD. 5 produtos cadastrados.

Webhooks → 07-INTEGRACOES/n8n → atualiza status do pedido em 01-FUNIL/AGENDADO / 01-FUNIL/PEDIU DADOS.

Status que importam pro agente:
- 11 — agendado
- 13 — pago
- Outros — devolvido / cancelado
