---
title: Kill Point Turn-1 — onde 60% do tráfego morre
publish: true
---

# Kill Point Turn-1 (PT1 = 60-77% das perdas)

## Diagnóstico

Amostra real: 5.501 contatos / 24.473 mensagens (workspace 397015 — produção até 2026-05-09).

- **97,2% dos leads parados em PT1 sumiram** sem agendar
- **906 leads que disseram "quero comprar" sumiram** sem fechar
- **3.297 leads com dúvida explícita sumiram** sem resposta efetiva
- Mediana: lead fala 1x, vendedora fala 3x → **vendedora monologa, lead foge**
- Apenas 24 contatos (0,4%) tocaram PT2 antes de sumir

## O padrão fatal

```
LEAD turn-1: "Como funciona o protocolo de cápsulas + gel? 🌿."
VEND turn-1: "Oi {nome}, tudo bem? Aqui é a Jaiane do Flor da Pele 🌹"
LEAD turn-2: [silêncio permanente]
```

Lead clicou no anúncio. Mensagem auto-preenchida saiu. Vendedora **cumprimentou em vez de responder à pergunta**. Lead pensou: *"essa pessoa não leu o que pedi"* e foi embora. **Velocidade de saída altíssima** (mediana 1 incoming = lead nunca volta).

## A regra de ouro pra Jaiane no turn-1

**ENTREGUE PRIMEIRO O QUE FOI PEDIDO + PIVÔ PARA QUALIFICAÇÃO NA MESMA MENSAGEM.**

### Exemplo correto

Cliente: "Como funciona o protocolo?"

Jaiane: "Oi $contact.firstname! O kit tem cápsula (toma de manhã) + gel íntimo (à noite). 5M R$467 · 8M R$627 · 12M R$767 — frete grátis e você paga na entrega 🌹 Você está sentindo mais o quê: calor/insônia, humor/energia ou libido/íntimo?"

### Por que funciona

1. Responde direto o que cliente pediu (info do protocolo + preço)
2. Reforça âncora positiva (frete grátis + COD)
3. Pivô pra qualificação numa pergunta única
4. Sem monólogo — mensagem ÚNICA

## Variações de turn-1 a reconhecer

Cliente chega via auto-fill do Meta CTWA com mensagens tipo:

- "Olá! Tenho interesse e queria mais informações, por favor."
- "Como funciona o protocolo de cápsulas + gel?"
- "Qual valor?"
- "Quanto custa?"
- "Tenho interesse, gostaria de saber o valor."
- "Bom dia! Qual o valor? Quanto tempo demora para chegar?"

**Trate "qual valor" como INTENT COMPRA**, não objeção. 94% das objeções "OUTROS" eram pedido de valor mal classificado.

## NÃO mandar áudio direto no turn-1

Workflow E1 já manda 2 áudios (boas-vindas + autoridade COD) automaticamente como mensagens 2 e 3 da PT1. A IA Jaiane só entra a partir do momento que cliente RESPONDE a essas 4 mensagens iniciais.
