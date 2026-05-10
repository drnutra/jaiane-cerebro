---
fonte: matriz-cfs-tags-lifecycle-2026-05-09.md + PT1 audit (60% perda turn-1 + ghost) + handoff sessão 3
data_coleta: 2026-05-09
ultima_validacao: 2026-05-09
expira_em: 2026-08-07
status: verificado
escopo: spec do workflow Re-engager pra Diego criar manualmente no respond.io 413594
---

# Workflow Re-engager — escala 30min/2h/8h/24h/72h

**Workspace:** 413594 · **Canal:** 487339 (WhatsApp 9525)
**Objetivo:** recuperar 60% perda PT1 (lead chega via CTWA, não responde primeiro turno).

## Trigger

**Tipo:** Tag adicionada
**Tag:** `in_funil`
**Condições adicionais:** `passou_e1` adicionada (workflow boas-vindas terminou) E lead NÃO respondeu (lifecycle ainda em PARTE 1).

## Estrutura

```
[Trigger: tag passou_e1 adicionada]
   ↓
[Wait 30 min]
   ↓
[Branch: lead respondeu? — checagem via CF última mensagem do contact tipo=contact]
   ├─ SIM → Stop Workflow
   └─ NÃO ↓
[Send msg #1 — texto curto leve]
   ↓
[Wait 1h 30min]
   ↓
[Branch: respondeu?] — SIM=Stop, NÃO↓
[Send msg #2 — áudio Jaiane curto + texto]
   ↓
[Wait 6h]
   ↓
[Branch: respondeu?] — SIM=Stop, NÃO↓
[Send msg #3 — texto + reforço COD]
   ↓
[Wait 16h]
   ↓
[Branch: respondeu?] — SIM=Stop, NÃO↓
[Send msg #4 — texto última tentativa]
   ↓
[Wait 48h]
   ↓
[Branch: respondeu?] — SIM=Stop, NÃO↓
[Add Tag: no_response]
[Update Lifecycle: SEM RESPOSTA]
[Add Comment time: "Lead esfriou — 5 follow-ups sem resposta"]
[Stop Workflow]
```

## Mensagens (texto canônico DR NUTRA — tom Jaiane)

### MSG 1 — 30 min depois (toque leve)
```
$contact.firstName, sumiu por aí? 🌹

Quando puder, me fala o que tá te incomodando MAIS hoje pra eu te orientar do jeito certo 💕
```

### MSG 2 — 2h depois (áudio + texto)

**Áudio:** reusar `01-AUDIO-boas-vindas-jaiane-v3.mp3` ou `02-AUDIO-autoridade-cod-jaiane-v3.mp3` (já uploaded no canal 487339 do workflow PT1).

**Texto após áudio:**
```
Tô aqui, $contact.firstName 💕

Sem pressa, tá? Quando der, me responde até em áudio se for mais fácil 🌹
```

### MSG 3 — 8h depois (reforço COD)
```
$contact.firstName, lembrando: você só paga quando o kit chegar na sua mão 📦

Frete grátis, abre e confere antes — sem risco ❤️ 

Posso te mostrar o protocolo certo pro que você sente?
```

### MSG 4 — 24h depois (última tentativa)
```
$contact.firstName, vou ficar por aqui se você quiser conversar 🌹

Se mudar de ideia, é só me chamar — sem cobrança, sem pressão 💕
```

### Após 72h sem resposta
- Tag: `no_response`
- Lifecycle: `SEM RESPOSTA`
- Comment timeline: "Lead esfriou — 5 follow-ups sem resposta. Última msg: $contact.last_message"
- Stop workflow

## Como Diego cria no respond.io 413594

1. Sidebar esquerda → **Workflows** (ícone fluxograma)
2. Clica **"+ Adicionar Workflow"**
3. Nome: `🔁 RE-ENGAGER PT1 (escala 30m-72h)`
4. **Trigger** → **Tag adicionada** → seleciona `passou_e1`
5. Adiciona **Wait** → **30 minutes**
6. Adiciona **Branch** → condição: "Conversa atualizada: última mensagem foi do contato"
   - SIM → Stop Workflow
   - NÃO → continua
7. Adiciona **Send Message** → cola MSG 1
8. Repete blocos Wait/Branch/Send pra MSG 2, 3, 4
9. Final: **Add Tag** `no_response` + **Update Lifecycle** `SEM RESPOSTA` + **Add Comment**

## Bloqueio resolvido (matriz):
- Lifecycle `SEM RESPOSTA` precisa existir. Per matriz pendente. Diego cria via Configurações > Lifecycle Stages.
