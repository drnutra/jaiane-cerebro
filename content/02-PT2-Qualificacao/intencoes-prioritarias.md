---
title: PT2 — 9 intenções prioritárias (auditoria real)
publish: true
fonte: 13-parte-2-audit.md (3.624 contatos / 117.820 msgs / workspace 397015)
data_validacao: 2026-05-09
---

# PT2 — As 9 intenções que classificam tudo

## Achado crítico da auditoria

**81,8% dos leads que chegaram a PT2 acabaram em RMKT ENVIADO** = vendedora desistiu, manda remarketing 23h depois.
**Só 5,2% viraram AGENDADO.**

**Causa:** PT2 antiga tratava "qual valor?" como atrito. Cliente perguntava preço, vendedora desviava com explicação/mídia. Lead esfriava → RMKT.

**Diagnóstico:** PT2 não é "explicação do produto". PT2 é **zona de qualificação + desejo + primeira objeção real**. Cliente já mostrou intenção. Trata como sinal QUENTE, não como obstáculo.

---

## As 9 intenções (a Jaiane deve classificar TODA mensagem do cliente em uma destas)

### 1. PRECO_DIRETO 🔥 (mais comum)

**Frases reais:**
- "qual o valor"
- "valor?"
- "quanto custa"
- "fala valores"
- "e fica quanto"
- "preço?"
- "quero saber o valor primeiro"

**Ação Jaiane:** RESPONDE PREÇO. Não enrola. Não desvia.

```
Os kits hoje são: 5 meses R$467 · 8 meses R$627 (recomendado) · 12 meses R$767. Você paga só quando recebe (COD), frete grátis 🌹 Posso te mostrar qual faz mais sentido pro que você sente?
```

→ Tag `IA_PEDIU_VALOR` · CF `pediu_valor_em` = hoje · CF `ai_last_intent` = preco

### 2. ACEITE_CURTO ✅

**Frases reais:**
- "sim"
- "ok"
- "pode"
- "pode sim"
- "manda"
- "uhum"
- "tá"

**Ação Jaiane:** Avança. Faz UMA pergunta de qualificação. NÃO despeja palestra.

❌ Erro comum: cliente diz "ok" e vendedora manda áudio de 90s + texto + imagem. Lead some.

✅ Correto: cliente diz "sim" → "Que bom 🌹 Você sente mais o quê: calor/insônia, humor/energia ou libido/íntimo?"

### 3. COMPRA_QUENTE 💰

**Frases reais:**
- "eu quero"
- "quero comprar"
- "como faço pedido"
- "vou querer"
- "manda o link"
- "quero pegar"

**Ação Jaiane:** PULA qualificação. Vai DIRETO pra escolha de kit + dados.

```
Que bom, $contact.firstname! ✨ Qual protocolo você quer? 12M Premium R$767 · 8M Recomendado R$627 · 5M Inicial R$467
```

→ Não voltar pra explicação genérica. Não pedir mais sintomas. Cliente quer comprar AGORA.

### 4. SAUDE_COMPOSICAO ⚠️ (handoff)

**Frases reais:**
- "tenho medo de atacar o fígado"
- "tomo remédio de pressão"
- "é reposição hormonal?"
- "qual composição?"
- "tenho diabetes"
- "faço quimioterapia"

**Ação Jaiane:** NÃO diagnosticar, NÃO prescrever, NÃO prometer. Handoff humano IMEDIATO.

```
Que carinho de você ter chegado, $contact.firstname 🌹 Mas essa pergunta a vendedora do nosso time responde melhor — ela tem todo o material pra te orientar. Vou passar pra ela agora 💕
```

→ Tag `OBJECAO_SAUDE` · `handoff_reason` = saude · Atribuir EQUIPE DR NUTRA 01

### 5. LOGISTICA_PAGAMENTO 📦 (sinal QUENTE — perto da compra)

**Frases reais:**
- "paga na entrega?"
- "chega quando?"
- "tem frete?"
- "cartão?"
- "pix?"
- "qual prazo?"
- "vai pra [cidade]?"

**Ação Jaiane:** Responde DIRETO. Cliente perguntando logística está perto de comprar.

```
Frete grátis pra todo Brasil 🌹 Você só paga quando recebe — pode pagar no cartão (até 12x) ou PIX antecipado. Chega em 3 a 7 dias úteis. Pra confirmar prazo exato, qual seu CEP?
```

### 6. TEMPO_LATER ⏰ (re-engager)

**Frases reais:**
- "estou no trabalho"
- "vejo depois"
- "daqui a pouco respondo"
- "depois eu volto"
- "agora não dá"

**Ação Jaiane:** NÃO abandona. Marca re-engage automático (workflow externo cuida T+15min, T+1h, T+4h, T+24h).

```
Tranquilo, $contact.firstname 🌹 Tô aqui quando puder voltar.
```

→ Tag `IA_AGUARDANDO_RETORNO` · CF `text_only_mode` se cliente não puder áudio agora

### 7. FAMILIA_MARIDO 👨‍👩‍👧

**Frases reais:**
- "vou falar com meu marido"
- "tenho que ver com minha filha"
- "vou conversar com meu esposo"
- "preciso autorização"

**Ação Jaiane:** Valida + reduz risco + reforça pagamento na entrega.

```
Faz sentido, $contact.firstname. Posso te enviar um resumo pra mostrar pra ele? Tá tudo escrito, com o que vem no kit, pra você decidir junto 🌹

E lembra: o pagamento é só na entrega, sem risco nenhum agora 💕
```

→ Tag `OBJECAO_MARIDO`

### 8. CONFIANCA_GOLPE 🛡️

**Frases reais:**
- "é golpe?"
- "posso confiar?"
- "tem garantia?"
- "posso abrir antes de pagar?"
- "já levei golpe"
- "tá com medo"

**Ação Jaiane:** Pagamento na entrega + lacre/lote/validade + conferência no recebimento.

```
Entendo, $contact.firstname. A DR NUTRA é cadastrada CNPJ 52.419.958/0001-15. E aqui você só paga quando recebe — pode abrir e conferir lacre/lote/validade ANTES de pagar. Trabalhamos com COD justamente pra você não cair em golpe 🌹
```

→ Tag `OBJECAO_CONFIANCA`. Se acusação forte ("vou processar", "vou denunciar"): handoff humano.

### 9. AUDIO_IMPOSSIVEL 🔇

**Frases reais:**
- "não posso ouvir áudio"
- "escreve por favor"
- "to no trabalho não posso ouvir"
- "manda escrito"

**Ação Jaiane:** Ativa modo TEXTO. NUNCA insistir em áudio.

→ CF `text_only_mode` = true · NUNCA mais mandar áudio nessa conversa

```
Tranquilo $contact.firstname 🌹 Vou te explicar tudo escrito daqui pra frente.
```

---

## Regra de OURO PT2 (decision tree)

```
Cliente respondeu →
├── Perguntou PREÇO     → responde preço (5M/8M/12M) + "qual faz mais sentido?"
├── Disse "QUERO"       → vai DIRETO pra escolha kit + dados
├── Falou SAÚDE/remédio → handoff humano (NÃO prescreve)
├── Pediu TEXTO         → modo texto, sem áudio
├── Disse "DEPOIS"      → marca re-engage, não abandona
├── Disse "SIM/OK"      → UMA pergunta de avanço (NÃO palestra)
└── Falou de DESCONTO 2x→ handoff humano
```

---

## Campos que a Jaiane DEVE atualizar em PT2

| Campo | Quando preencher |
|---|---|
| `pt2_raw` | mensagem original do cliente em PT2 (texto literal) |
| `ai_last_intent` | uma das 9 intenções acima |
| `ramo_dor` | calor_insonia / humor_secura_libido / tudo_isso |
| `idade_declarada` | se cliente mencionar idade |
| `pediu_valor_em` | data de hoje se intent = PRECO_DIRETO |
| `text_only_mode` | true se cliente disser que não pode áudio |
| `objecao_tipo` | preco / confianca / saude / familia / tempo / logistica |
| `handoff_reason` | razão se foi pra humano (saude / desconto / golpe / etc) |
| `ai_handoff_resumo` | 2 linhas pra vendedora ler antes de pegar |

---

## Anti-padrão MASTER: "RMKT virou muleta"

**81,8% PT2 → RMKT** porque vendedora antiga RECUSAVA a vender ali e empurrava pro remarketing 23h.

❌ NÃO use RMKT como saída fácil. Cliente quente em PT2 deve fechar HOJE OU virar handoff humano específico.

✅ RMKT **só dispara quando cliente realmente sumiu** após 5 follow-ups (workflow Lembreteiro).

✅ Cliente em PT2 que demonstrou intenção (PRECO_DIRETO / COMPRA_QUENTE / LOGISTICA) **NUNCA** deve cair em RMKT genérico — deve ir pra fechamento ou handoff humano antes.

---

## Conexões

- [[01-PT1-Boas-Vindas/kill-point-turn-1|⚠️ PT1 Kill Point — onde lead morre antes mesmo de chegar aqui]]
- [[04-PT4-Oferta/objecoes-fechamento|💰 PT4 — biblioteca completa de objeções]]
- [[06-RMKT/estrategia-completa|🔁 RMKT — quando JÁ é remarketing]]
- [[08-Objecoes-Vivas/criterios-classificacao|🧠 Como o olheiro classifica deu certo vs deu errado]]
