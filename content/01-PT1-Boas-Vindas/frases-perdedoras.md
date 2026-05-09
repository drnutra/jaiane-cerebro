---
title: Anti-padrões PT1 — frases que matam o lead
publish: true
---

# Frases que MATAM o lead na PT1

NÃO use essas frases — derivadas de análise de 5.351 leads que sumiram em PT1.

## Cumprimento sozinho (sem responder)

❌ "Oi Maria, tudo bem? Aqui é a Jaiane do Flor da Pele 🌹" + parar

Em 6/6 amostras de ghosts, o lead chegou pedindo info ("Como funciona?") e a vendedora respondeu apenas com cumprimento. **Lead some no turn-2.**

## Desviar pergunta de preço pra qualificação fechada

❌ "Primeiro me conta seu sintoma" sem mencionar valor

Em 8/8 conversas onde cliente pediu valor, vendedora desviou e lead sumiu. Cliente se sentiu ignorado.

✅ Em vez disso: **passar valor + pivô pra qualificação na mesma mensagem** (ver `frases-vencedoras.md`).

## Mandar 3+ mensagens em sequência (monólogo)

❌ Padrão típico do dataset:
```
LEAD: "Qual valor?"
VEND-msg1: "Oi tudo bem? Aqui é a Jaiane 🌹"
VEND-msg2: "Você está com sintomas da menopausa?"
VEND-msg3: "Posso te mandar um áudio explicando direitinho?"
VEND-msg4: [áudio de 90s]
LEAD: [silêncio]
```

WhatsApp é canal **conversacional**, não broadcast. Cada mensagem unidirecional sem resposta queima atenção.

✅ **Regra:** uma resposta da Jaiane por uma resposta do lead. Se lead não responde em 3 min, **uma** sondagem leve, depois automação assume.

## Forçar script qualificador depois de "quero comprar"

❌ Lead disse "quero comprar" → Jaiane responde "primeiro me conta seu sintoma"

**906 leads disseram "quero comprar" e 100% sumiram.** Lead com pressa sente fricção e foge.

✅ Branch: se intent = COMPRA na mensagem 1, pular qualificação e ir direto pra:
- Apresentar 3 kits + preços
- "Qual te chama mais atenção?"
- Após escolha, pedir CEP + nome → checkout

## Mandar áudio sem cliente pedir

❌ Cliente: "Qual valor?"
❌ Jaiane: [áudio de 90s]

Cliente que pediu info em texto **não está pedindo áudio**. Mandar áudio força esforço e quebra ritmo.

✅ Áudios são parte do workflow E1 automatizado (2 áudios canônicos). FORA disso, só mandar áudio se cliente pedir.
