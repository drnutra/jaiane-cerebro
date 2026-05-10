---
fonte: 00-ESTRUTURA-FUNIL-COMPLETA.md + Instructions Jaiane v3 + matriz-cfs-tags-lifecycle-2026-05-09.md
data_coleta: 2026-05-09
ultima_validacao: 2026-05-09
expira_em: 2026-08-09
status: verificado
escopo: spec pra Diego construir manualmente no respond.io 413594
---

# Workflow PT5 — PEDIDO DE DADOS

**Workspace:** 413594 · **Canal:** WhatsApp 9525 · **AI Agent:** 1094908

## Cabeçalho do workflow

| Campo | Valor |
|---|---|
| **Nome** | `🤖 PT5 — PEDIDO DE DADOS` |
| **Trigger** | Etiqueta de contato atualizada → Tag adicionada → `passou_e4` |

## Estrutura completa

```
[Gatilho] Tag adicionada = passou_e4
   ↓
[1]  Atualizar Ciclo de Vida → PEDINDO DADOS
   ↓
[2]  Esperar 3 segundos
   ↓
[3]  Enviar mensagem (ÁUDIO)  ← 01-AUDIO-pedido-cep-dados.mp3
   ↓
[4]  Esperar 5 segundos
   ↓
[5]  Enviar mensagem (TEXTO)  ← parabéns + lista de campos
   ↓
[6]  Esperar 3 segundos
   ↓
[7]  Atualizar Tag → adicionar passou_e5 (ou skip — IA vai capturar dados)
```

⚠️ **Captura dos dados é feita pela IA Jaiane** (AI Agent 1094908) que extrai os campos da resposta livre do cliente e atualiza os custom fields:
- `nome_completo`, `email`, `cpf`, `cep`, `endereco_rua`, `endereco_numero`, `endereco_bairro`, `endereco_cidade`

Quando todos os 8 campos estão preenchidos, IA dispara workflow Braip (a criar) que cria pedido COD via API.

## Conteúdo de cada step

### Step 3 — ÁUDIO
`/Users/diegoribeiro/Desktop/AUDIOS_FINAIS_FUNIL/PARTE-5-E5-PEDIDO-DADOS/01-AUDIO-pedido-cep-dados.mp3` (470KB)

### Step 5 — TEXTO

```
🎉 Parabéns pela decisão ✅

Agora vou precisar dessas informações para inserir seu pedido no sistema.

•⁠ ⁠Nome
•⁠ ⁠Email (caso tenha)
•⁠ ⁠CPF (Emissão de nota)
•⁠ ⁠Cep do seu endereço
•⁠ ⁠Rua
•⁠ ⁠Nº
•⁠ ⁠Bairro
•⁠ ⁠Cidade
```

### Step 7 — Atualizar Tag (opcional)
- Adicionar `dados_completos` SE quiser tag final pra trigger Braip
- OU deixar IA setar quando confirmar os 8 CFs preenchidos

## Como construir no respond.io

1. **Workflows** → **+ Adicionar workflow** → nome `🤖 PT5 — PEDIDO DE DADOS`
2. **Gatilho:** Etiqueta de contato atualizada → Tag adicionada → `passou_e4`
3. Steps [1] a [7] em ordem
4. **Publicar**

## Próximo workflow após PT5

**Workflow Braip COD** (a criar) — trigger: tag `dados_completos`
- HTTP Request POST → Braip API criar pedido COD com todos os dados do contato
- Atualizar CF `braip_order_id`
- Atualizar Tag `enviado_braip`
- Atualizar Lifecycle `AGENDADO`
- Atribuir Para vendedora humana (round-robin) pra ligação de confirmação
