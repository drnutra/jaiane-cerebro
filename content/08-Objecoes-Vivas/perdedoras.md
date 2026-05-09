---
title: Frases PERDEDORAS — anti-padrões aprendidos
publish: true
ultima_atualizacao_olheiro: 2026-05-09
---

# Frases perdedoras (anti-padrões — auto-atualizado)

> Este arquivo é **auto-atualizado** pelo olheiro n8n a cada 1h. NÃO editar manual sem coordenar.

Frases reais usadas pela Jaiane (ou vendedora antiga) que precederam **SUMIÇO do lead**. NÃO usar.

## Como o olheiro alimenta esse arquivo

```
Pseudocódigo do cron (n8n - WF-Olheiro):
A cada 1h:
  1. Pegar últimas N conversas com final_result = "sumiu"
  2. Extrair última mensagem da Jaiane antes do silêncio
  3. Agrupar por padrão (lemma + structure)
  4. Adicionar ao arquivo com contagem de ocorrências
  5. Git push → vault publica
  6. AI Agent re-sincroniza
```

## Anti-padrões conhecidos (base PT2 PDF + diagnóstico crítico)

### Anti-pattern #1 — Cumprimento sozinho no turn-1 (88% dos ghosts)

```
Oi $contact.firstname, tudo bem? Aqui é a Jaiane do Flor da Pele 🌹
```

(quando enviada SOZINHA, sem resposta à pergunta do cliente)

- Frequência de sumiço: 4.843 casos
- Anti-uso: turn-1 contra cliente que pediu info específica
- Substituir por: ENTREGAR info pedida + pivô qualificação na MESMA mensagem

### Anti-pattern #2 — Bombardeio (3+ mensagens sem resposta)

Padrão típico:
```
VEND-msg1: "Oi tudo bem? 🌹"
VEND-msg2: "Você está com sintomas da menopausa?"
VEND-msg3: "Posso te mandar um áudio?"
VEND-msg4: [áudio 90s]
```

- Frequência: maioria das conversas que sumiram em PT1
- Regra: **uma mensagem da Jaiane por uma mensagem do cliente**

### Anti-pattern #3 — Ignorar intent COMPRA

Cliente disse "quero comprar" → Jaiane responde "primeiro me conta seu sintoma"

- 906 casos: 100% sumiram
- Regra: se intent = COMPRA, pular qualificação, ir direto pra escolha de kit + dados

### Anti-pattern #4 — Resposta vazia ao pedido de valor

Cliente: "Qual valor?"
Jaiane: "Oi $contact.firstname, tudo bem?"

- Frequência: 8/8 conversas com PRECO_VALOR_DIRETO sumidas
- Regra: passar valor + pivô na mesma mensagem (NÃO desviar)

### Anti-pattern #5 — Mandar áudio sem cliente pedir

Cliente: [pergunta em texto]
Jaiane: [áudio de 90s]

- Cliente que pediu info em texto NÃO está pedindo áudio
- Quebra ritmo, força esforço
- Regra: áudios só se cliente pedir OU se forem os 2 áudios canônicos do workflow E1

### Anti-pattern #6 — Re-engager genérico sem personalização

```
Oi! Vi que você se interessou e não respondeu. Quer continuar?
```

- Sem nome, sem contexto da dor, sem urgência
- Substituir por: re-engager com nome + dor específica + projeção temporal

## Inserções automáticas pelo olheiro

[Auto-atualizado abaixo conforme novos anti-padrões são detectados]
