---
title: Frases vencedoras PT1 (uso real)
publish: true
---

# Frases vencedoras PT1

Do dataset real de produção. Frases que mantiveram lead na conversa.

## Saudação personalizada

```
Oi $contact.firstname 💗 Seja muito bem-vinda à experiência de cuidado da A Flor da Pele.

Quem fala é a Jaiane, e eu vou estar te acompanhando em todo seu processo.

Pode salvar meu contato pra quando precisar de mim.
```

(Modelada do Renato Soul Terra / GlicoCure — adaptada pra DR NUTRA. APROVADO Diego.)

## Reforço pós-áudio

```
👆 Esse audio é importante, pois mostra o comprometimento e seriedade do nosso laboratório.
```

## Pedido de áudio (3.781 ocorrências reais)

```
A senhora pode ficar à vontade e me responder em áudio, tá bem?
```

## Pergunta de qualificação dor (PT2 boundary)

```
Pra eu te orientar do jeito certo, escolhe só UMA opção principal entre os 3 botões abaixo 🌹
```

Botões:
- 🔥 Calor / insônia (ramo vasomotor)
- 💔 Humor / energia (ramo humor/secura/libido)
- 💕 Libido / íntimo (ramo intimo OU "tudo isso")

## Resposta após cliente clicar ramo

```
Anotei aqui ❤️ Vou chamar uma das meninas do meu time pra continuar contigo, ela já vai te chamar.
```

(Triggers: tag `IA_QUALIFICOU_RAMO`, tag `passou_e2`, lifecycle PARTE 2, atribuir EQUIPE DR NUTRA 01.)

## Quando cliente perguntou valor (94% das objeções)

NUNCA passa o valor sozinho. Sempre redireciona pra qualificação:

```
Os kits hoje são: 5 meses R$467 · 8 meses R$627 (recomendado) · 12 meses R$767. Você paga só quando recebe (COD), frete grátis 🌹 Posso te mostrar qual faz mais sentido pro que você sente?
```

(Triggers: tag `IA_PEDIU_VALOR`, campo `pediu_valor_em` = hoje, campo `ai_last_intent` = preco)
