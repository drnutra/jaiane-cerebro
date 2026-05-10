---
title: Workflows tags e lifecycle
publish: true
tags: [workflow, tags, lifecycle]
---

# Workflows, tags e lifecycle

## Regra central

Enviar mensagem nao atualiza tag nem lifecycle. Toda transicao precisa de workflow ou acao propria.

## Tag IDs

| Etapa | Tag ID |
|---|---:|
| PT1 | 3923048 |
| PT2 | 3923047 |
| PT3 | 3923046 |
| PT4 | 3923044 |
| PEDIU DADOS | 3923051 |

## Lifecycle IDs

| Etapa | Lifecycle ID |
|---|---:|
| PARTE 1 | 773534 |
| PARTE 2 | 773535 |
| PARTE 3 | 773536 |
| PARTE 4 | 773715 |
| PEDIU DADOS | 773719 |

## Transicao de etapa

Ao avancar etapa:

1. Remover tag anterior.
2. Aplicar tag nova.
3. Atualizar lifecycle quando necessario.
4. Registrar resumo operacional.

## Re-engager

Cadencia:

- T+15min.
- T+1h.
- T+4h.
- T+24h.

Tom: mais firme a cada tentativa. Nao ser passiva. Nao inventar oferta restrita sem criterio de remarketing.
