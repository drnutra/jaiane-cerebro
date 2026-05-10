---
fonte: cruzamento de 00-ESTRUTURA-FUNIL-COMPLETA.md (Diego) + PT2 PDF real (3624 contatos / 117820 msgs) + RESPONDIO-GITHUB-AI-AGENT-AUDIT.md + 24 CFs/9 tags atuais 413594
data_coleta: 2026-05-09
ultima_validacao: 2026-05-09
expira_em: 2026-08-09
status: verificado
---

# Matriz definitiva — Custom Fields · Tags · Lifecycle (DR NUTRA / 413594)

Cruzamento de 4 fontes + dados reais funil. Otimizado pro mínimo possível sem perder rastreabilidade.

## Resumo numérico

| Tipo | Total | Criar | Manter | Deletar | Renomear |
|---|---|---|---|---|---|
| Lifecycle | 10 | +2 | 8 atuais | 0 | 0 |
| Custom Fields | 32 | +10 | 22 atuais | 2 | 2 |
| Tags | 20 | +13 (todas — workspace virgem) | 0 | 0 (limpo) | 0 |

→ Tags atuais (9 IA): vou recriar com nomenclatura unificada `e1_*/e2_*/dor_*` em vez de `IA_*`. Mais limpo, alinhado com 5 PARTES do funil.

---

## 1️⃣ LIFECYCLE STAGES (10)

Mantém 8 atuais nativos do 413594 + adiciona 2 que faltam. Nomenclatura "PARTE 1-4" é canônica DR NUTRA (equipe usa há meses, dados PT2 PDF mostram).

| # | Stage | Quando seta | Quem seta |
|--:|---|---|---|
| 1 | NOVO LEAD | Lead chega via CTWA, conversation aberta | Trigger workflow E1 |
| 2 | PARTE 1 | Saudação enviada (após áudio boas-vindas) | Workflow E1 |
| 3 | PARTE 2 | Áudio qualificação enviado, aguardando áudio cliente | Workflow E2 |
| 4 | PARTE 3 | IA classificou ramo dor (calor/humor/tudo) | AI Agent (Update Lifecycle) |
| 5 | PARTE 4 | Apresentação concluída, pergunta 0-10 | Workflow E3 → E4 |
| 6 | PEDINDO DADOS | Cliente escolheu kit, IA pediu CPF/CEP/etc | AI Agent / Workflow E4 → E5 |
| 7 | AGENDADO | Pedido COD criado no Braip | Workflow E5 (HTTP Braip OK) |
| 8 | PAGO | Webhook Braip status 13 confirmado | Workflow webhook Braip |
| 9 | **SEM RESPOSTA** ⚠️ NOVO | 3 follow-ups sem resposta | Workflow re-engager final |
| 10 | **HUMANO PRONTO** ⚠️ NOVO | IA precisa de ligação humana | AI Agent (handoff médico/objeção pesada) |

**Stages que NÃO entram (do audit GitHub mas vou descartar):**
- "Em qualificação", "Qualificado", "Oferta enviada", "Fechamento" → redundantes com PARTE 1-4 (genéricos vs específicos do funil real DR NUTRA)
- "Cliente" → cobre PAGO

---

## 2️⃣ CUSTOM FIELDS (32)

### 2.1 MANTER (22 — já criados, alinhados)

#### CTWA / Atribuição (5)
| Slug | Tipo | Quando seta |
|---|---|---|
| `ctwa_clid` | text | Webhook CTWA chegada (last-touch) |
| `ctwa_clid_first` | text | Primeira chegada (first-touch) |
| `ctwa_ad_id` | text | Webhook |
| `ctwa_adset_id` | text | Webhook |
| `ctwa_campaign_id` | text | Webhook |

#### CAPI / Tracking (4)
| Slug | Tipo | Quando seta |
|---|---|---|
| `capi_event_id_lead` | text | Workflow E2 dispara Lead pro CAPI |
| `capi_event_id_purchase` | text | Workflow webhook Braip pago |
| `capi_last_status` | list | n8n após cada envio CAPI |
| `capi_last_sent_at` | date | n8n após sucesso |

#### Funil / IA (4)
| Slug | Tipo | Quando seta |
|---|---|---|
| `funil_stage` | list (`novo`/`e1`/`e2`/`e3_calor`/`e3_humor`/`e3_tudo`/`e4`/`e5`/`agendado`/`pago`) | Cada workflow ao concluir etapa |
| `ai_paused_until` | text | Vendedora ativou "pausa IA" |
| `ai_summary` | text | AI Agent atualiza a cada turno |
| `ai_handoff_resumo` | text | AI Agent quando faz handoff humano |

#### Comercial — pedido (5)
| Slug | Tipo | Quando seta |
|---|---|---|
| `cpf` | text | E5 cliente envia |
| `cep` | text | E5 cliente envia |
| `kit_escolhido` | list (~~5M/8M/12M/RMKT_327~~) | E4 botão protocolo |
| `braip_order_id` | text | Workflow E5 após HTTP Braip OK |
| `pago_em` | date | Webhook Braip pago |

⚠️ **`kit_escolhido` precisa ter valores REVISADOS** (ver seção 2.3 RENOMEAR)

#### IA específicos (4)
| Slug | Tipo | Quando seta |
|---|---|---|
| `ramo_dor` | list (`calor_insonia`/`humor_secura_libido`/`tudo_isso`) | E2 IA classifica áudio cliente |
| `ai_last_intent` | list (saudacao/preco/duvida/compra/objecao_*) | A cada turno IA |
| `pediu_valor_em` | date | Cliente perguntou preço (97% objeções) |
| `respondeu_audio` | checkbox | Cliente respondeu em áudio (signal forte) |

⚠️ **`ramo_dor` precisa ter valores REVISADOS** (ver seção 2.3)

### 2.2 CRIAR (10 — novos, alinhados ao doc Diego)

| Slug | Tipo | Quando seta | Por quê |
|---|---|---|---|
| `nivel_comprometimento` | number | E4 cliente responde 0-10 | Branch high-touch (8-10) vs nurture (0-7) |
| `modalidade_pagamento` | list (`antecipado_pix`/`entrega_cod`) | E4 áudio modalidade | Workflow Braip diferente cada |
| `nome_completo` | text | E5 cliente envia | NF Braip |
| `email` | text (opcional) | E5 cliente envia | Email marketing pós-venda |
| `endereco_rua` | text | E5 | Logística |
| `endereco_numero` | text | E5 | Logística |
| `endereco_bairro` | text | E5 | Logística |
| `endereco_cidade` | text | E5 | Logística |
| `objecao_atual` | list (`preco`/`marido`/`pensar`/`confianca`/`tempo`/`outros`) | IA detecta objeção em qualquer parte | Roteia áudio certo (top objeções: 97% OUTROS, 6% MARIDO, 5% PENSAR, 4% PRECO, 2% CONFIANCA) |
| `tem_pagado_antes` | checkbox | E1 lookup contatos antigos | Recompra vs novo |

### 2.3 RENOMEAR / AJUSTAR VALORES (2)

| Slug atual | Valores atuais | Valores corretos | Razão |
|---|---|---|---|
| `kit_escolhido` | `5M / 8M / 12M / RMKT_327` | `5m_inicial / 8m_completo / 12m_premium / rmkt_327` | Alinha com nomenclatura doc + permite filtro semântico |
| `ramo_dor` | `vasomotor / humor / intimo / todos` | `calor_insonia / humor_secura_libido / tudo_isso` | Doc Diego usa esses 3 nomes em Branch E3 |

→ Ação: deletar e recriar, OU update via API se possível.

### 2.4 DELETAR (2 — substituídos por separados)

| Slug | Razão |
|---|---|
| `endereco_entrega` | Substituído por `endereco_rua/numero/bairro/cidade` separados (Braip exige) |
| `idade_declarada` | Não aparece no funil real PT2 (3624 contatos) — equipe não captura formalmente. Mantém só se for usado pra fora-ICP, mas é redundante com filtro de campanha CTWA |

---

## 3️⃣ TAGS (20)

Workspace 413594 tem 9 tags `IA_*` que vou substituir por nomenclatura unificada `e1_*/e2_*/dor_*` (mais limpa, alinhada com PARTES E1-E5).

### Tags por grupo

#### Progressão funil (6)
| Tag | Quando aplica |
|---|---|
| `in_funil` | CTWA chegada (E1 trigger) |
| `passou_e1` | E1 completo (áudio boas-vindas enviado) |
| `passou_e2` | E2 completo (áudio qualificação enviado) |
| `passou_e3` | E3 completo (apresentação ramo) |
| `passou_e4` | E4 completo (kit escolhido) |
| `dados_completos` | E5 todos campos coletados |

#### Ramo dor (3)
| Tag | Quando |
|---|---|
| `dor_calor` | IA classifica áudio E2 → vasomotor |
| `dor_humor` | IA classifica → humor/secura/libido |
| `dor_tudo` | IA classifica → todos |

#### Compromisso (2)
| Tag | Quando |
|---|---|
| `compromisso_alto` | E4 resposta 0-10 ≥ 8 |
| `compromisso_baixo` | E4 resposta 0-10 ≤ 7 |

#### Kit / Modalidade (5)
| Tag | Quando |
|---|---|
| `kit_12m` | E4 botão 12M |
| `kit_8m` | E4 botão 8M |
| `kit_5m` | E4 botão 5M |
| `pix_antecipado` | E4 modalidade PIX |
| `cod_entrega` | E4 modalidade COD |

#### Estado / Handoff (4)
| Tag | Quando |
|---|---|
| `enviado_braip` | E5 HTTP Braip OK |
| `cliente_pago` | Webhook Braip pago |
| `handoff_ligacao` | IA pede ligação humana (objeção pesada / dúvida saúde) |
| `no_response` | 3 follow-ups sem resposta |

→ **Total: 20 tags**

### 3.1 Tags NÃO criadas (movidas pra CF)
- ❌ `objecao_preco`, `objecao_marido`, `objecao_pensar`, `objecao_confianca`, `objecao_tempo`, `objecao_outros` → viraram CF `objecao_atual` (list) — 1 valor por contato é mais útil pra roteamento
- ❌ `cliente_recompra` → vira CF `tem_pagado_antes` (checkbox)
- ❌ `fora_icp_idade` → não aparece no funil real, descartado
- ❌ `IA_PEDIU_VALOR`, `IA_RESPONDEU_AUDIO` → viram CFs `pediu_valor_em` (date) e `respondeu_audio` (checkbox) — já criados

### 3.2 Tags atuais a deletar (9 IA_*)
```
IA_PT1_INICIADA, IA_PEDIU_VALOR, IA_RESPONDEU_AUDIO, IA_QUALIFICOU_RAMO,
HANDOFF_HUMANA_PRONTA, OBJECAO_MARIDO, OBJECAO_CONFIANCA, FORA_ICP_IDADE, NO_RESPONSE
```
→ Substituídos pela nomenclatura unificada acima.

---

## 4️⃣ DIFF DE EXECUÇÃO

### CFs
- **Criar (10):** `nivel_comprometimento`, `modalidade_pagamento`, `nome_completo`, `email`, `endereco_rua`, `endereco_numero`, `endereco_bairro`, `endereco_cidade`, `objecao_atual`, `tem_pagado_antes`
- **Deletar (2):** `endereco_entrega`, `idade_declarada`
- **Renomear/atualizar valores (2):** `kit_escolhido` (valores), `ramo_dor` (valores)
- **Manter (22):** intactos

### Tags
- **Deletar (9):** todas IA_* atuais
- **Criar (20):** todas novas com nomenclatura unificada

### Lifecycle stages
- **Adicionar (2):** `SEM RESPOSTA`, `HUMANO PRONTO`
- **Manter (8):** intactos (NOVO LEAD / PARTE 1-4 / PEDINDO DADOS / AGENDADO / PAGO)

---

## 5️⃣ ORDEM DE EXECUÇÃO (quando aprovado)

1. Deletar 2 CFs obsoletos via Playwright UI (API não tem DELETE)
2. Criar 10 CFs novos via API (rápido)
3. Atualizar valores `kit_escolhido` + `ramo_dor` via Playwright UI (API não atualiza valores de list)
4. Deletar 9 tags antigas via API DELETE
5. Criar 20 tags novas via API
6. Adicionar 2 lifecycle stages via Playwright UI
7. Validar contagens finais via API

→ Tempo estimado: 8-12min se Playwright cooperar.

---

## 6️⃣ Pontos abertos (Diego confirma)

| # | Pergunta | Default sugerido |
|---|---|---|
| 1 | Preço Kit 5M é **R$ 447** (doc) ou **R$ 467** (CLAUDE.md raiz)? | Aguardo |
| 2 | Voice ID Jaiane atual: `XKF0hQaeLT6EMGkd5RjT` (doc) ou `q8xTUDpioW6pyCkV3aAx` (CLAUDE)? | Aguardo |
| 3 | Mantenho `idade_declarada` ou deleto? | Deleto (não usado no funil real) |
| 4 | Stage `HUMANO PRONTO` se chama assim ou `LIGAR` (alinhar com tag `LIGOU` do PT2 PDF)? | `LIGAR` é melhor — alinha com nomenclatura real |
