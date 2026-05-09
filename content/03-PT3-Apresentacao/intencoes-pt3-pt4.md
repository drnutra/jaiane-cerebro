---
title: PT3 + PT4 — Auditoria consolidada (intenções, anti-padrões, regras)
publish: true
fonte: 06-parte-3-audit.md + 05-parte-4-audit.md + 11-agendado-audit.md + 08-abandono-dados-audit.md
data_validacao: 2026-05-09
---

# PT3 + PT4 — Auditoria consolidada

## Veredicto

PT3 morre antes da escolha. PT4 não morre por falta de interesse — morre por **incoerência de oferta** + abandono pós-kit + AGENDADO sem virar PAGO.

---

## PT3 — Números (3.057 contatos / 105.041 mensagens)

| Resultado | Qtd | % |
|---|---:|---:|
| 🔴 RMKT ENVIADO | 2.492 | 81,5% |
| 🟡 Escolheu kit em PT4 | 454 | 14,9% |
| 🟢 AGENDADO | 176 | 5,8% |
| 🔴 ABANDONO DADOS | 84 | 2,7% |
| 🟢 PAGO | 4 | 0,13% |

**Problema raiz:** o campo `pt3` virou flag burra. Top respostas: "sim", "pode", "pode sim", "ok", "sim pode". Não guarda dor, intenção, objeção, nível de compromisso nem motivo de queda.

### Distribuição de intenções dentro do PT3

| Intent | Contatos | Sinal |
|---|---:|---|
| `aceite_binario` (sim/ok/pode) | 2.306 | permissão pra avançar (NÃO encerrar) |
| `quer_valores` | 189 | mandar V5 direto |
| `compra_quente` | 45 | pular pra escolha/dados |
| `recusa/adiamento` | 80 | re-engager OU projeção temporal |
| `duvida_produto` | 22 | esclarecer técnico (sem alegação médica) |
| `outro_texto` | 415 | classificar individualmente |

### Sinais brutos no universo PT3 (frequência total)

```
preço:        1.907 contatos
pagamento:      785
confiança:      711
escolha kit:    675
tempo/pensar:   433
dados/checkout: 409
compra quente:  350
marido/família: 347
frete/prazo:    305
saúde/interação:239
caro/sem $:     160
áudio/texto:    118
cancelamento:    86
```

### Regra de ouro PT3 (decision tree)

```
Cliente respondeu →
├── "sim/ok/pode"         → permissão pra avançar (UMA pergunta de qualificação, NÃO palestra)
├── "qual valor/quanto"   → V5 direto (5M R$467 / 8M R$627 / 12M R$767), NÃO voltar pra explicação
├── "eu quero/quero compr"→ PULAR qualificação, ir pra escolha/dados
├── "pior" pós projeção   → ir pra PT4 (quebra emocional ativada)
├── compromisso 0-7       → PROJEÇÃO TEMPORAL antes da oferta
├── compromisso 8-10      → FECHAMENTO DIRETO (sem mais explicação)
├── Saúde/remédio/doença  → HANDOFF HUMANO (não responder)
└── Áudio impossível      → modo TEXTO (text_only_mode = true)
```

---

## PT4 — Números (460 contatos / 21.975 mensagens)

| Resultado | Qtd | % |
|---|---:|---:|
| 🔴 RMKT | 305 | 66,3% |
| 🟢 AGENDADO | 97 | 21,1% |
| 🔴 ABANDONO DADOS | 32 | 7,0% |
| 🟢 PAGO | 1 | 0,22% |

**Conversão AGENDADO → PAGO: 1,03%.** Catastrófico.

### Distribuição de kit escolhida no histórico (TUDO LEGADO)

| Kit escolhido | % | Status no V5 |
|---|---:|---|
| 3 meses | 66,7% | ❌ MORTO |
| 6 meses | 19,3% | ❌ MORTO |
| 12 meses | 13,9% | ✅ ÚNICO válido |

**ERRO MAIS CARO:** 86% das escolhas estão em kits que NÃO EXISTEM MAIS no V5. Cliente esperava preço antigo, cobradora chegou cobrando outro = recusa garantida.

### Sinais brutos no universo PT4

```
escolha kit:   457
pagamento:     262
preço:         244
dados/checkout:239
frete/prazo:   124
confiança:     122
compra quente:  93
tempo/pensar:   60
marido/família: 49
saúde/interação:33
caro/sem $:     21
áudio/texto:    21
cancelamento:   18
```

### Regra de ouro PT4

```
Cliente em PT4 →
├── Escolheu kit (texto livre OU botão) → registrar kit_escolhido + ir pra modalidade
├── Disse "boleto"                       → CORRIGIR: NÃO aceita boleto. Oferece COD ou PIX
├── Pediu prazo/frete                    → "Frete grátis 3-7 dias úteis. Qual seu CEP?"
├── "Caro/sem dinheiro"                  → Parcelamento 12x OU 5M como entrada (R$467)
├── "Vou falar com marido"               → Resumo pro marido + reforça COD
├── "É golpe?"                           → CNPJ + COD + site oficial
├── Saúde/remédio                        → HANDOFF HUMANO
└── 8 dados de uma vez                   → ❌ ERRADO. Pede 1-2 por vez progressivamente
```

**MUDANÇA crítica do que estava no Instructions anterior:**
- ❌ ANTES: "Pedir todos dados em UMA mensagem"
- ✅ AGORA: "Pedir dados PROGRESSIVAMENTE — começar com nome+CEP, depois CPF, depois rua/nº/bairro/cidade"

Razão: 7% abandonaram em PT4 = 32 de 460. Hipótese: lista de 8 campos assusta.

---

## Pós-PT4 — Estágios críticos

### AGENDADO (189 contatos)

- 185/189 com `braip_order_id` (97,9%)
- 92/189 SEM pt4 anotado (48,7%)
- Entre os anotados, **90,7% kit LEGADO** proibido
- 9/189 tentaram cancelar pós-agendamento
- `last_ctwa_clid` em apenas 5,3% — Meta cego!

**Bloqueio CRÍTICO:** Jaiane NÃO PODE mover lifecycle pra AGENDADO sem ter:
- ✅ `kit_escolhido` (V5: 5m_inicial / 8m_completo / 12m_premium)
- ✅ `modalidade_pagamento` (cod_entrega / pix_antecipado)
- ✅ Dados mínimos (nome + CPF + CEP + endereço completo)
- ✅ `ctwa_clid` capturado pra Meta CAPI

### ABANDONO_DADOS (121 contatos)

- 37 escolheram kit
- 84% dos que escolheram estavam em kit LEGADO (3M/6M)
- 9 chegaram a ter `braip_order_id`

**Diagnóstico:** cliente foi fundo mas travou no checkout — fricção, preço divergente, OU dados demais de uma vez.

**Resposta da Jaiane se cliente abandona:** workflow Lembreteiro reage em T+15min com mensagem específica de retomada de checkout (não genérica).

### FINAL_DO_FUNIL (125 contatos — categoria especial "perdeu_valores")

- 102 tinham `pt3` preenchido
- **0 tinham `pt4`** preenchido

**Diagnóstico:** cliente aceitou ver valores mas NÃO escolheu kit. Tipo perfil: hesitante / comparando.

**Estratégia recuperação:**
- ❌ NÃO RMKT genérico (já é uma fase frustrante)
- ✅ Workflow específico "perdeu_valores": áudio Jaiane personalizado lembrando da projeção temporal + oferta menor (5M R$467) com reforço de COD

---

## NUNCA ALIMENTAR O AGENT COM (lista crítica anti-alucinação)

### Kits proibidos (V5 mata todos)
- ❌ Kit 1M (R$ 247)
- ❌ Kit 2+1
- ❌ Kit 3M
- ❌ Kit 6M

### Modalidades proibidas
- ❌ Boleto bancário (não aceita)
- ❌ "Mensagem não é gravada" (frase antiga, não usar)

### Promessas proibidas
- ❌ Cura, "remédio", reposição hormonal natural
- ❌ "Salvar casamento" como gancho
- ❌ Garantia agressiva de resultado
- ❌ Comparação com medicamento

### Práticas proibidas
- ❌ Ameaçar Serasa / cobrança jurídica cedo
- ❌ Áudios `cdn.respond.io/*` se workflow exige `production--bucket.s3-accelerate.amazonaws.com.com`

### Kit RMKT 327
- ❌ NUNCA mencionar no fluxo principal PT1→PT5
- ✅ Só workflow remarketing dirigido oferece

---

## Campos que Jaiane DEVE atualizar

### PT3
| Campo | Quando |
|---|---|
| `pt3_raw` | mensagem original do cliente em PT3 |
| `nivel_comprometimento` | número 0-10 da resposta projeção |
| `compromisso_alto` (tag) | resposta 8-10 |
| `compromisso_baixo` (tag) | resposta 0-7 |
| `ramo_dor` | calor / humor / tudo |
| `permissao_valores` (bool) | true se cliente aceitou ver valores |
| `ai_last_intent` | uma das 9 intenções |
| `perdeu_valores` (tag) | aceitou valor mas não escolheu kit |
| `handoff_reason` | razão do handoff |

### PT4
| Campo | Quando |
|---|---|
| `pt4_raw` | mensagem original em PT4 |
| `kit_escolhido` | 5m_inicial / 8m_completo / 12m_premium |
| `kit_5m`/`kit_8m`/`kit_12m` (tag) | tag específica |
| `modalidade_pagamento` | cod_entrega / pix_antecipado |
| `pediu_boleto` (tag) | true se cliente pediu boleto (corrigir) |
| `dados_status` | nome / cpf / cep / endereco_completo |
| `cep` | quando enviado |
| `checkout_abandonado` (tag) | se parou no meio dos dados |
| `pedido_braip_status` | criado / processando / agendado / pago |
| `ai_handoff_resumo` | 2 linhas pra vendedora |

---

## Conexões

- [[02-PT2-Qualificacao/intencoes-prioritarias|⬅️ PT2 — 9 intenções]]
- [[04-PT4-Oferta/precos-V5|💰 Tabela V5 oficial]]
- [[04-PT4-Oferta/objecoes-fechamento|🛡️ Biblioteca completa de objeções]]
- [[06-RMKT/estrategia-completa|🔁 RMKT — kit-específico vs genérico]]
- [[07-Pos-Venda/cobranca-soft|🚚 Pós-venda + cobrança]]
- [[00-HUB-MAE|🧠 Hub mãe]]
