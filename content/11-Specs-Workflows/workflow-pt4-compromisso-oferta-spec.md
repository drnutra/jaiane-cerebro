---
fonte: 00-ESTRUTURA-FUNIL-COMPLETA.md + Instructions Jaiane v3 + matriz-cfs-tags-lifecycle-2026-05-09.md
data_coleta: 2026-05-09
ultima_validacao: 2026-05-09
expira_em: 2026-08-09
status: verificado
escopo: spec pra Diego construir manualmente no respond.io 413594
---

# Workflow PT4 — COMPROMISSO + OFERTA

**Workspace:** 413594 · **Canal:** WhatsApp 9525 · **AI Agent:** 1094908

## Cabeçalho do workflow

| Campo | Valor |
|---|---|
| **Nome** | `🤖 PT4 — COMPROMISSO + OFERTA` |
| **Trigger** | Etiqueta de contato atualizada → Tag adicionada → `passou_e3` |

## Estrutura completa (todos os steps em ordem)

```
[Gatilho] Tag adicionada = passou_e3
   ↓
[1]  Atualizar Ciclo de Vida → PARTE 4
   ↓
[2]  Esperar 5 segundos
   ↓
[3]  Enviar mensagem (TEXTO)  ← compromisso 0-10
   ↓
[4]  Esperar 30 segundos       ← gap pra cliente responder com número
   ↓
[5]  Enviar mensagem (ÁUDIO)  ← 02-AUDIO-preco-anvisa-cod.mp3
   ↓
[6]  Esperar 8 segundos
   ↓
[7]  Enviar mensagem (ÁUDIO)  ← 03-AUDIO-oferta-protocolo-8-meses.mp3
   ↓
[8]  Esperar 8 segundos
   ↓
[9]  Enviar mensagem (ÁUDIO)  ← 04-AUDIO-downsell-5-meses-frete-gratis.mp3
   ↓
[10] Esperar 5 segundos
   ↓
[11] Enviar mensagem (IMAGEM) ← 05-IMAGEM-oferta-3-kits.png
   ↓
[12] Esperar 3 segundos
   ↓
[13] Enviar mensagem (TEXTO)  ← condição especial campanha (1 linha)
   ↓
[14] Esperar 2 segundos
   ↓
[15] Enviar mensagem (TEXTO)  ← tabela 3 protocolos com preços
   ↓
[16] Esperar 8 segundos
   ↓
[17] Enviar mensagem (ÁUDIO)  ← 08-AUDIO-modalidade-pix-vs-cod.mp3
   ↓
[18] Esperar 5 segundos
   ↓
[19] Enviar mensagem (TEXTO)  ← duas formas pagamento
   ↓
[20] Esperar 3 segundos
   ↓
[21] Fazer uma pergunta (BOTÕES)  ← 3 quick replies
   ↓
[22] Atualizar Tag → adicionar passou_e4
```

## Conteúdo de cada step

### Step 3 — TEXTO compromisso 0-10

```
Agora eu preciso te perguntar algo importante, e quero que você me responda com sinceridade:

👉 *De 0 a 10, qual o seu nível de comprometimento em fazer esse cuidado direitinho e resolver esse problema de uma vez por todas?*

Me responde só com o número. 👇
```

⚠️ "tratamento" → "esse cuidado" (veto DR NUTRA aplicado).

### Step 5 — ÁUDIO
`/Users/diegoribeiro/Desktop/AUDIOS_FINAIS_FUNIL/PARTE-4-E4-COMPROMISSO/02-AUDIO-preco-anvisa-cod.mp3` (730KB)

### Step 7 — ÁUDIO
`…/PARTE-4-E4-COMPROMISSO/03-AUDIO-oferta-protocolo-8-meses.mp3` (2.0MB)

### Step 9 — ÁUDIO
`…/PARTE-4-E4-COMPROMISSO/04-AUDIO-downsell-5-meses-frete-gratis.mp3` (1.4MB)

### Step 11 — IMAGEM
`…/PARTE-4-E4-COMPROMISSO/05-IMAGEM-oferta-3-kits.png`

### Step 13 — TEXTO condição especial

```
🔥 *CONDIÇÃO ESPECIAL — CAMPANHA PROTOCOLO PRO+40* 🔥
```

### Step 15 — TEXTO tabela 3 protocolos

```
*👑 PROTOCOLO PREMIUM - 12 MESES*
12 Potes de À Flor da Pele
(6 Cápsulas + 4 Gotas + 2 Géis)
de ~R$ 2.190,00~ por apenas *R$ 767,00* à vista no PIX
ou *12x de R$ 78,90* no cartão
+ Acompanhamento personalizado incluso
+ Frete Grátis

*⭐ PROTOCOLO COMPLETO - 8 MESES (RECOMENDADO)*
8 Potes de À Flor da Pele
(4 Cápsulas + 3 Gotas + 1 Gel)
de ~R$ 1.490,00~ por apenas *R$ 627,00* à vista no PIX
ou *12x de R$ 64,50* no cartão
+ Acompanhamento personalizado incluso
+ Frete Grátis

*✅ PROTOCOLO INICIAL - 5 MESES*
5 Potes de À Flor da Pele
(3 Cápsulas + 2 Gotas)
de ~R$ 990,00~ por apenas *R$ 447,00* à vista no PIX
ou *12x de R$ 45,99* no cartão
+ Acompanhamento personalizado incluso
+ Frete Grátis

*Prazo de entrega: 3 a 7 dias úteis ✈️👇*
```

⚠️ Preços V5 conferem com CLAUDE.md global (5M=467, 8M=627, 12M=767). Ajuste no áudio (Renato fala 397/697 e clone Jaiane diz 447/627/767 — checar áudio 03/04 antes).

### Step 17 — ÁUDIO
`…/PARTE-4-E4-COMPROMISSO/08-AUDIO-modalidade-pix-vs-cod.mp3` (2.3MB)

### Step 19 — TEXTO duas formas pagamento

```
A gente trabalha com duas formas de pagamento, viu minha querida:

✅ *Pagamento antecipado* — envio rápido pelos Correios Express, de 5 a 10 dias úteis.

✅ *Pagamento na entrega* — você paga somente quando receber em casa, porém o envio leva um pouco mais de tempo, de 10 a 20 dias úteis.

Escuta com atenção o áudio aí em cima pra entender direitinho as duas opções. 👆📢👆
```

### Step 21 — Fazer uma pergunta (3 BOTÕES)

**Pergunta:**
```
Qual protocolo você prefere, minha querida? 👇
```

**Tipo:** Multiple Choice (Quick Reply WABA)
**Salvar resposta em CF:** `kit_escolhido`
**3 opções:**

| Botão | Texto | Valor salvo |
|---|---|---|
| 1 | `👑 12 MESES PREMIUM` | `12m_premium` |
| 2 | `⭐ 8 MESES COMPLETO` | `8m_completo` |
| 3 | `💗 5 MESES INICIAL` | `5m_inicial` |

Adicionar tags por escolha (Branch implícito da própria pergunta — usar action "Atualizar Tag" no fluxo de cada resposta):
- 12m_premium → tag `kit_12m`
- 8m_completo → tag `kit_8m`
- 5m_inicial → tag `kit_5m`

### Step 22 — Atualizar Tag
- Ação: Adicionar Etiqueta
- Tag: `passou_e4`

## Como construir no respond.io

1. **Workflows** → **+ Adicionar workflow** → nome `🤖 PT4 — COMPROMISSO + OFERTA`
2. **Gatilho:** Etiqueta de contato atualizada → Tag adicionada → `passou_e3`
3. Clicar `+` abaixo do gatilho e adicionar steps na ordem [1] a [22]
4. **Guardar** após cada bloco de 5 steps (não perder trabalho)
5. **Publicar** quando tudo OK
