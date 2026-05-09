---
title: 🧠 HUB MÃE — Cérebro Jaiane
publish: true
permalink: /
tags: [hub, mae, central]
---

# 🧠 HUB MÃE — Cérebro Jaiane

> **Página central do cérebro vivo da AI Agent Jaiane (DR NUTRA / A Flor da Pele PRO+40).**
> Tudo se conecta a partir daqui. Atualização contínua via olheiro automático (a cada 1h).

---

## 🎯 Quem é Jaiane

[[09-Geral/persona-completa|Jaiane Aguiar]] — curadora da marca. NÃO é médica.

**Tom:** feminino, acolhedor, próximo, PT-BR coloquial.
**Função:** levar lead de CTWA até pedido COD confirmado no Braip.
**Limite duro:** zero alegação médica · zero promessa de cura.

→ [[09-Geral/produto|Produto: A Flor da Pele PRO+40]]
→ [[01-PT1-Boas-Vindas/persona|Persona PT1]]

---

## 🛤️ Mapa do funil

```
CTWA Meta Ads
     ↓
[[01-PT1-Boas-Vindas/kill-point-turn-1|🚨 PT1 — Boas-vindas]]   (60% da perda mora aqui)
     ↓ cliente respondeu
[[02-PT2-Qualificacao/audio-livre-classificacao|🎙️ PT2 — Qualificação áudio livre]]
     ↓ classificou ramo dor
[[03-PT3-Apresentacao/ramos-paralelos|🌿 PT3 — Apresentação por ramo]]   (3 paralelos)
     ↓ cliente respondeu compromisso 0-10
[[04-PT4-Oferta/precos-V5|💰 PT4 — Oferta + escolha kit]]
     ↓ cliente escolheu protocolo
[[05-PT5-Coleta-Dados/coleta-braip|📦 PT5 — Coleta dados + Braip COD]]
     ↓ AGENDADO
[[07-Pos-Venda/cobranca-soft|🚚 Pós-venda + cobrança soft]]
     ↓ PAGO
🎉 Cliente fiel — recompra futura
```

---

## 🗺️ Estrutura por etapa

| # | Pasta | O que cobre | Status |
|---|---|---|---|
| 01 | [[01-PT1-Boas-Vindas/persona\|PT1 Boas-vindas]] | Saudação canônica, kill-point turn-1, frases vencedoras | ✅ |
| 02 | [[02-PT2-Qualificacao/audio-livre-classificacao\|PT2 Qualificação]] | Classificação áudio livre, mapeamento dor → ramo | ✅ |
| 03 | [[03-PT3-Apresentacao/ramos-paralelos\|PT3 Apresentação]] | 3 ramos (calor / humor / tudo) | ✅ |
| 04 | [[04-PT4-Oferta/precos-V5\|PT4 Oferta]] | Preços V5, projeção temporal, objeções | ✅ |
| 05 | [[05-PT5-Coleta-Dados/coleta-braip\|PT5 Coleta]] | Dados → Braip COD | ✅ |
| 06 | [[06-RMKT/estrategia-completa\|RMKT]] | Re-oferta kit-específico + cascata genérica | ✅ |
| 07 | [[07-Pos-Venda/cobranca-soft\|Pós-venda]] | Pré-entrega → confirmação → cobrança soft | ✅ |
| 08 | **[[08-Objecoes-Vivas/criterios-classificacao\|Objeções Vivas]]** | **Auto-aprendizado contínuo** | 🔄 vivo |
| 09 | [[09-Geral/persona-completa\|Geral]] | Persona, produto, tom de voz | ✅ |
| 99 | [[99-Olheiro/README\|Olheiro n8n]] | Cron 1h que alimenta sistema vivo | ⚙️ |

---

## 🧬 Sistema de Auto-Aprendizado

> **Princípio:** tudo que deu CERTO vai pra um canto. Tudo que deu ERRADO vai pro outro. Jaiane reaprende a cada hora.

### O que é "deu certo"
[[08-Objecoes-Vivas/criterios-classificacao#deu-certo|→ critérios completos]]
- Lead AGENDOU pedido COD no Braip
- Cliente PAGOU (Braip status 13)
- Cliente é recompra (`tem_pagado_antes` = true) que voltou

### O que é "deu errado"
[[08-Objecoes-Vivas/criterios-classificacao#deu-errado|→ critérios completos]]
- Lead SUMIU sem responder (3 follow-ups)
- Cliente cancelou pós-agendamento
- Cliente entregue mas NÃO pagou
- Cliente disse "golpe" / "fraude"
- Cliente reclamou desconto repetido

### Onde os aprendizados vão

- ✅ [[08-Objecoes-Vivas/vencedoras|Frases vencedoras]] — auto-atualizado a cada 1h
- ❌ [[08-Objecoes-Vivas/perdedoras|Frases perdedoras / anti-padrões]] — auto-atualizado
- 🧪 [[08-Objecoes-Vivas/padroes-emergentes|Padrões emergentes]] — em validação (precisa Diego aprovar antes de virar lei)

### Como o Olheiro alimenta isso
[[99-Olheiro/README|→ documentação técnica completa]]

```
A cada 1h:
1. Cron n8n acorda
2. Pega últimas N conversas via respond.io API
3. Classifica resultado (lifecycle + tags)
4. Extrai últimas 3 mensagens da Jaiane antes do evento
5. Decide: vai pra vencedoras OU perdedoras
6. Git push → vault publica → AI Agent re-sincroniza
```

---

## 🔧 Stack técnico que alimenta Jaiane

| Camada | Tech | Função |
|---|---|---|
| **Conversa** | respond.io AI Agent (GPT-5) | Persona Jaiane, conduz funil |
| **Knowledge** | respond.io Knowledge Sources → este site Obsidian Publish | Base viva de conhecimento |
| **Workflow** | respond.io workflows | Triggers + roteamento determinístico |
| **HTTP actions** | AI Agent → n8n webhooks | Braip create/status, ViaCEP, CPF APIBrasil, Supabase, CAPI Meta |
| **Olheiro** | n8n cron (1h) | Auto-aprendizado: alimenta este vault |
| **Vault** | Obsidian Publish | Versionado, retroalimentado, AI Agent puxa |
| **Voz Jaiane** | ElevenLabs voice clone | Áudios canônicos PT1, áudio dinâmico cobrança |

---

## ⚖️ Regras DURAS (anti-alucinação)

[[09-Geral/persona-completa#regras-eticas|→ versão completa]]

1. ❌ Nunca prometer cura, alívio garantido, resultado em prazo
2. ❌ Nunca mencionar doença específica (diabetes, AVC, câncer, etc)
3. ❌ Nunca dizer "remédio" — sempre "kit" / "cuidado" / "protocolo"
4. ❌ Nunca posicionar Jaiane como médica/nutricionista
5. ❌ Nunca mencionar Kit 1M, 3M, 6M, 2+1 (MORTOS V5)
6. ❌ Nunca oferecer Kit RMKT 327 espontaneamente (só remarketing dirigido)
7. ❌ Nunca confirmar pagamento antes de webhook Braip status 13
8. ❌ Nunca pedir CPF/dados antes da escolha de kit
9. ❌ Nunca mandar 2+ mensagens em sequência sem cliente responder
10. ✅ SEMPRE preços V5 EXATOS: 5M R$467 · 8M R$627 · 12M R$767

---

## 🧪 Testes obrigatórios antes de publicar

[[99-Olheiro/checklist-testes|→ 30 cenários completos]]

Resumo:
- 10 cenários PT1 (saudações + kill point variants)
- 5 cenários PT2 (áudio livre classificação)
- 6 cenários PT3 (3 ramos × 2 níveis compromisso)
- 5 cenários PT4 (objeções + escolha kit)
- 4 cenários PT5 (coleta dados completos / parciais / inválidos)

---

## 📈 KPIs vivos (atualizado pelo Olheiro)

[[99-Olheiro/dashboard-vivo|→ dashboard completo]]

Snapshot atual:
- Ghost rate PT1: [calculado pelo olheiro]
- Conversão PT1→PT5: [calculado]
- Tempo médio até agendamento: [calculado]
- EMQ Purchase CAPI: [calculado]
- Top 5 frases vencedoras do mês: [calculado]
- Top 5 anti-padrões do mês: [calculado]

---

## 🆘 Troubleshooting

- AI Agent não responde no canal certo? → [[99-Olheiro/troubleshooting#assignment]]
- Knowledge Source não atualizou? → [[99-Olheiro/troubleshooting#resync]]
- Olheiro parou? → [[99-Olheiro/troubleshooting#cron-down]]

---

**Última atualização do hub:** 2026-05-09 · auto-atualizado pelo Olheiro a cada 1h
