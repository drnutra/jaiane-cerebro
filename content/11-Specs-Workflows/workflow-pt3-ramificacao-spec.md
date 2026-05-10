---
fonte: AI Agent v3 Instructions + AUDIOS_FINAIS_FUNIL/PARTE-3-E3-RAMIFICACAO + 12-playbook-canonico-funil.md
data_coleta: 2026-05-09
ultima_validacao: 2026-05-09
expira_em: 2026-08-07
status: verificado
escopo: spec do workflow PT3 pra Diego criar manualmente no respond.io 413594
---

# Workflow PT3 — Ramificação por dor

**Workspace:** 413594 · **Canal:** 487339 (WhatsApp 9525) · **AI Agent:** 1094908

## Trigger

`AI Agent action: Acionar Workflow` chamado pelo AI Agent v3 quando lead clica/digita ramo de dor em PT2.

Variável de entrada: `$contact.ramo_dor` (List: `calor_insonia` | `humor_secura_libido` | `tudo_isso`)

## Estrutura geral

```
[Trigger]
  ↓
[Update Lifecycle: PARTE 3]
  ↓
[Add Tag: passou_e2 + dor_<ramo>]
  ↓
[Branch: $contact.ramo_dor]
  ├─ calor_insonia → [RAMO A] (6 steps)
  ├─ humor_secura_libido → [RAMO B] (6 steps)
  └─ tudo_isso → [RAMO C] (6 steps)
  ↓ (3 ramos convergem)
[Add Tag: passou_e3]
  ↓
[Trigger AI Agent: continua PT4 com áudios oferta]
```

---

## RAMO A — calor/insônia (6 elementos)

| # | Tipo | Asset (path local) | Wait pós | Notas |
|---|---|---|---|---|
| A1 | Áudio | `~/Desktop/AUDIOS_FINAIS_FUNIL/PARTE-3-E3-RAMIFICACAO/RAMO-A-CALOR-INSONIA/01-AUDIO-calor-insonia-jaiane.mp3` (1.1MB) | 3s | dor "espelho" — Jaiane fala da dor da cliente |
| A2 | Imagem | `…/RAMO-A-CALOR-INSONIA/02-IMAGEM-infografico-calor-insonia.png` (1.9MB) | 2s | infográfico mecanismo |
| A3 | Áudio | `…/RAMO-A-CALOR-INSONIA/03-AUDIO-educacao-3-frentes-calor.mp3` (2.0MB) | 3s | explica 3 frentes do produto |
| A4 | Vídeo | `…/RAMO-A-CALOR-INSONIA/04-VIDEO-prova-social-1.mp4` (26MB) ⚠️ | 4s | prova social cliente real |
| A5 | Vídeo | `…/RAMO-A-CALOR-INSONIA/05-VIDEO-prova-social-2.mp4` (15MB) | 4s | segunda prova social |
| A6 | Áudio | `…/RAMO-A-CALOR-INSONIA/06-AUDIO-pos-provas-calor.mp3` (1.5MB) | — | reforço pós-provas, prepara PT4 |

⚠️ **Vídeo A4 = 26MB.** WhatsApp limit é 16MB (vídeo) ou 100MB (documento). Pode falhar. **Necessário comprimir antes de uploadar** — alvo ≤14MB. Diego confirma se já tem versão comprimida.

---

## RAMO B — humor/secura/libido (6 elementos)

| # | Tipo | Asset | Wait pós | Notas |
|---|---|---|---|---|
| B1 | Áudio | `…/RAMO-B-HUMOR-SECURA-LIBIDO/01-AUDIO-humor-secura-libido-jaiane.mp3` (1.3MB) | 3s | |
| B2 | Imagem | `…/RAMO-B-HUMOR-SECURA-LIBIDO/02-IMAGEM-infografico-humor-secura-libido.png` (1.8MB) | 2s | |
| B3 | Áudio | `…/RAMO-B-HUMOR-SECURA-LIBIDO/03-AUDIO-educacao-3-frentes-humor-secura-libido.mp3` (2.1MB) | 3s | |
| B4 | Vídeo | `…/RAMO-B-HUMOR-SECURA-LIBIDO/04-VIDEO-prova-social-1.mp4` (8.1MB) | 4s | dentro do limite |
| B5 | Vídeo | `…/RAMO-B-HUMOR-SECURA-LIBIDO/05-VIDEO-prova-social-2.mp4` (15MB) | 4s | dentro do limite |
| B6 | Áudio | `…/RAMO-B-HUMOR-SECURA-LIBIDO/06-AUDIO-pos-provas-humor-secura-libido.mp3` (1.5MB) | — | |

---

## RAMO C — tudo isso (6 elementos)

| # | Tipo | Asset | Wait pós | Notas |
|---|---|---|---|---|
| C1 | Áudio | `…/RAMO-C-TUDO-ISSO/01-AUDIO-tudo-isso-jaiane.mp3` (2.0MB) | 3s | |
| C2 | Imagem | `…/RAMO-C-TUDO-ISSO/02-IMAGEM-infografico-tudo-isso.png` (1.8MB) | 2s | |
| C3 | Áudio | `…/RAMO-C-TUDO-ISSO/03-AUDIO-educacao-3-frentes-tudo-isso.mp3` (2.0MB) | 3s | |
| C4 | Vídeo | `…/RAMO-C-TUDO-ISSO/04-VIDEO-prova-social-1.mp4` (7.5MB) | 4s | |
| C5 | Vídeo | `…/RAMO-C-TUDO-ISSO/05-VIDEO-prova-social-2.mp4` (15MB) | 4s | |
| C6 | Áudio | `…/RAMO-C-TUDO-ISSO/06-AUDIO-pos-provas-tudo-isso.mp3` (1.7MB) | — | |

---

## Como Diego cria no respond.io 413594

1. Sidebar respond.io → **Workflows** → **+ Add workflow**
2. Nome: `🤖 PT3 RAMIFICACAO POR DOR`
3. Trigger: **Conversation Updated** com filtro `Lifecycle = PARTE 2` E `Tag contains passou_e2`
4. Step 1: **Update Lifecycle** → `PARTE 3`
5. Step 2: **Branch** → condição `$contact.ramo_dor`
   - Branch 1: equals `calor_insonia` → executa A1-A6
   - Branch 2: equals `humor_secura_libido` → executa B1-B6
   - Branch 3: equals `tudo_isso` → executa C1-C6
6. Em cada branch, sequência de 6 steps **Send Message** (clica no clip pra anexar arquivo do desktop)
7. Entre cada Send Message, step **Wait** com tempo da tabela
8. Após convergir os 3 branches: step **Add Tag** `passou_e3`
9. Step final: **Trigger AI Agent** (Jaiane 1094908) — continua PT4

---

## ⚠️ Bloqueios pra Diego resolver antes de subir

1. **Vídeo A4 RAMO-A = 26MB** → comprimir pra ≤14MB (HandBrake / ffmpeg).
2. **Verificar se PT2 tem áudio uploaded** no respond.io 413594 (workflow boas-vindas avança pra PT2 quando cliente responde — quem manda o áudio qualificação?).
3. **Workflow PT2** ainda não existe — só PT1 (`1778339517052492`). Possíveis caminhos:
   - (a) AI Agent fala em texto, sem áudio canônico (perde força emocional)
   - (b) Criar workflow PT2 antes do PT3 — apenas 1 áudio + 1 texto
   - **Recomendado: (b)** — 5min de trabalho.

---

## Próximos workflows a especificar (em ordem)

- [ ] **PT2 qualificação** (1 áudio + 1 texto + espera resposta áudio livre)
- [x] **PT3 ramificação** (este arquivo)
- [ ] **PT4 oferta** (10 elementos, 3 botões kit)
- [ ] **PT5 dados** (1 áudio + 1 texto, captura nome/CPF/CEP/etc)
- [ ] **Re-engager** (escala 15min/1h/4h/23h/72h)
- [ ] **Vigia** (cuca leads parados >X horas)
- [ ] **Braip COD** (cria pedido pós-PT5 via webhook n8n)
