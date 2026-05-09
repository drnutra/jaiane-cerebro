---
title: Objeções de fechamento (8 categorias com scripts vencedores)
publish: true
---

# Biblioteca de objeções — scripts vencedores reais

Do dataset 3.624 contatos / 117.820 mensagens. Frases que VENCERAM cada objeção.

## 1. PRECO_VALOR_DIRETO (94% das "objeções")

**Sinal real:** cliente está PEDINDO preço, não rejeitando. Tratar como intent COMPRA.

### Padrão regex
`(qual\s+(o\s+)?valor|quanto\s+cust|preç|valor\s+(do|da|desse)|gostaria.*saber.*valor)`

### Resposta canônica
```
Os kits hoje são: 5 meses R$467 · 8 meses R$627 (recomendado) · 12 meses R$767. Você paga só quando recebe (COD), frete grátis 🌹 Posso te mostrar qual faz mais sentido pro que você sente?
```

## 2. TÁ CARO / NÃO POSSO PAGAR

### Frases reais que apareceram
- "Caro hem"
- "Achei muito caro"
- "Está um pouco caro pra mim"
- "Não posso pagar muito caro"
- "Tá apertado"

### Respostas vencedoras (do dataset, todas Superada=SIM)

```
Parcelado no cartão de crédito fica ruim, $contact.firstname?
```

```
Você não tem cartão pra parcelar em 12x?
```

```
Posso te mostrar o de 5 meses, é nossa entrada de R$467 — fica 12x R$48
```

```
Você tem 90 dias de garantia 🌹
```

## 3. VOU PENSAR / MAIS TARDE / DEPOIS

→ **Usar SEMPRE o script projeção temporal** (ver `projecao-temporal.md`).

## 4. VOU FALAR COM MEU MARIDO

### Frases reais
- "Vou falar com meu marido"
- "Vou conversar com meu esposo"
- "Segunda meu marido me passa o dinheiro"

### Resposta vencedora (NÃO argumentar contra estrutura familiar)

```
Faz sentido, $contact.firstname. Posso te enviar um resumo pra mostrar pra ele? Tá tudo escrito, com o que vem no kit, pra você decidir junto 🌹
```

Outra opção (followup leve no dia seguinte):
```
Bom dia minha querida 💕 Conseguiu falar com seu esposo? Vamos escolher seu protocolo?
```

## 5. ESTOU SEM MARIDO / SOU SEPARADA

### Resposta vencedora (DR NUTRA principle)

```
Esse cuidado é pra você primeiro, sentir você de novo. Marido vem depois 💕 Posso continuar?
```

## 6. CONFIANÇA / É GOLPE / TENHO MEDO

### Frases reais
- "É golpe?"
- "Tenho medo de não funcionar"
- "Levei golpe antes"
- "Pensei que era golpe"

### Resposta vencedora (CNPJ + COD elimina objeção)

```
Entendo, $contact.firstname. A DR NUTRA é cadastrada CNPJ 52.419.958/0001-15, e você só paga quando recebe (COD, frete grátis). Posso te mandar o site oficial pra conferir?
```

```
Minha linda, aqui você só vai pagar na entrega! 🌹
```

## 7. FUNCIONA MESMO? / TEM EFEITO?

### Resposta vencedora (composição técnica + sem promessa de cura)

```
O kit é 100% natural — feno-grego, L-arginina, taurina, zinco, vitaminas B6 e E + gel íntimo com centella. Sem hormônio. Cada mulher reage no seu tempo, mas a maioria sente diferença a partir de 30 dias 🌹
```

⚠️ **NUNCA prometer cura, eficácia médica, garantia de resultado.**

## 8. DOENÇA / REMÉDIO / SAÚDE

### Frases reais que disparam HANDOFF imediato
- "Tomo remédio de pressão"
- "Tenho diabetes"
- "Tireoide"
- "Faço reposição hormonal"
- "Posso tomar com meu remédio?"
- "Vai mexer com meu fígado?"

### Resposta canônica (NÃO responder, passar pra humana)

```
Que carinho de você ter chegado, $contact.firstname 🌹 Mas essa pergunta a vendedora do nosso time responde melhor — ela tem todo o material pra te orientar com calma. Vou passar pra ela agora 💕
```

→ Action: assign_to_team `EQUIPE DR NUTRA 01` + add_comment com resumo.

## 9. PRAZO / FRETE / QUANDO CHEGA

### Resposta canônica
```
Frete grátis pra todo Brasil 🌹 Você só paga quando recebe. Chega em 3 a 7 dias úteis. Pra confirmar prazo exato, qual seu CEP?
```

## 10. RECOMPRA / TÁ ACABANDO O KIT

### Resposta vencedora
```
Que bom, $contact.firstname! Pra continuar o protocolo, o de 8 meses tem o melhor custo-benefício (R$627). Posso fechar pra você?
```

(Atalho: pular qualificação, ir direto pra escolha + dados Braip.)

## TRIGGERS DE HANDOFF IMEDIATO (pular pra vendedora humana)

- Pediu LIGAÇÃO telefônica
- Disse "golpe", "fraude", "vou processar", "denuncia"
- Mencionou doença grave (câncer, AVC, depressão severa, problema cardíaco)
- Perguntou interação medicamentosa específica
- Pediu DESCONTO 2x ou mais
- Está em raiva forte
- Mandou áudio inaudível 2x
- É recompra (campo `tem_pagado_antes` = true)
