---
title: Frases VENCEDORAS — auto-atualizado pelo olheiro
publish: true
ultima_atualizacao_olheiro: 2026-05-09
---

# Frases vencedoras (atualizadas pelo olheiro)

> Este arquivo é **auto-atualizado** pelo olheiro n8n a cada 1h. NÃO editar manual sem coordenar.

Frases reais usadas pela Jaiane que precederam **AGENDAMENTO** ou **PAGAMENTO** do cliente. Ordenadas por frequência de sucesso.

## Como o olheiro alimenta esse arquivo

```
Pseudocódigo do cron (n8n - WF-Olheiro):
A cada 1h:
  1. Pegar últimas N mensagens via respond.io API
  2. Filtrar conversas com lifecycle = AGENDADO ou PAGO
  3. Extrair últimas 3 mensagens da Jaiane antes do evento
  4. Adicionar a este arquivo com timestamp + contexto
  5. Git push → vault publica
  6. AI Agent re-sincroniza Knowledge Source
```

## Padrões aprendidos (atualizados automaticamente)

### Pattern #1 — Projeção Temporal (vence PENSAR/TEMPO/CARO)

```
$contact.firstname, rapidinho: se tudo continuar do jeitinho que tá hoje — calorões, sono ruim e a libido lá embaixo — como você acha que vai estar daqui a 3 meses: melhor ou pior?
```

- Vezes vencida: 20 (PT2 PDF base)
- Última vez registrada: 2026-05-07
- Tags do cliente que reagiram bem: PENSAR, TEMPO, PRECO

### Pattern #2 — Quebrar objeção MARIDO ("estou sem")

```
Esse cuidado é pra você primeiro, sentir você de novo. Marido vem depois 💕 Posso continuar?
```

- Vezes vencida: 6
- Última vez: 2026-05-07
- Tags reativas: OBJECAO_MARIDO

### Pattern #3 — COD elimina objeção CONFIANÇA

```
Minha linda aqui você só vai pagar na entrega! 🌹
```

- Vezes vencida: 2
- Última vez: 2026-05-07
- Tags reativas: OBJECAO_CONFIANCA, "é golpe?"

### Pattern #4 — Parcelamento quebra objeção PREÇO

```
Parcelado no cartão de crédito fica ruim, $contact.firstname?
```

- Vezes vencida: 5
- Tags reativas: OBJECAO_PRECO

### Pattern #5 — Pergunta direta de compromisso (E4)

```
O que está te impedindo de fechar seu tratamento hoje, meu bem?
```

- Vezes vencida: 3
- Contexto: cliente em PARTE_4 com hesitação

### Pattern #6 — Recompra direta

```
Que bom! Pra continuar o protocolo, o de 8 meses tem o melhor custo-benefício (R$627). Posso fechar pra você?
```

- Vezes vencida: 2
- Contexto: lead com `tem_pagado_antes` = true

## Inserções automáticas pelo olheiro (próximos blocos)

[O olheiro vai inserindo abaixo conforme detecta novos padrões vencedores. Cada entrada terá timestamp.]
