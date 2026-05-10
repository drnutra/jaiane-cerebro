---
title: Integracoes e fonte de verdade
publish: true
tags: [integracoes, verdade]
---

# Integracoes e fonte de verdade

## respond.io

respond.io e a superficie operacional:

- inbox.
- conversa.
- lifecycle.
- tags.
- workflows.
- handoff.

## AI Agent

AI Agent e camada de conversa. Nao e backend completo.

## Workflows

Workflows executam logica deterministica:

- roteamento.
- follow-up.
- tags.
- lifecycle.
- disparos controlados.

## Braip

Braip e referencia para pedido e status comercial.

## Supabase

Supabase e fonte de verdade para estado longo, tracking, atribuicao e telemetria quando conectado ao fluxo.

## n8n

n8n orquestra integracoes externas e rotinas automaticas.

## Regra de verdade

Se a IA nao recebeu confirmacao de sistema, ela nao pode afirmar que pedido, pagamento, tag, lifecycle ou tracking foi atualizado.
