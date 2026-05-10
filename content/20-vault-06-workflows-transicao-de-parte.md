---
title: Vault curado - 06-WORKFLOWS/Transição de Parte
publish: true
tags: [vault, curado]
---

# Vault curado - 06-WORKFLOWS/Transição de Parte

---
tags: [workflow, transicao]
---
# Workflow: Transição de Parte

A cada avanço PT1→PT2→PT3→PT4→PEDIU DADOS executar 06-WORKFLOWS/Tag + Lifecycle.

## Sequência por transição
1. `mcp__respondio__remove_contact_tags` (tag da parte anterior)
2. `mcp__respondio__add_contact_tags` (tag da parte nova)
3. `mcp__respondio__update_contact_lifecycle` (se lifecycle mudou)
4. Atualiza nota em leads ativos
5. Atualiza JSON em `~/agente-jaiane/data/leads/<id>.json`
