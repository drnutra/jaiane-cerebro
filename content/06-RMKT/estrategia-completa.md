---
title: Estratégia RMKT — específico por kit + cascata genérica
publish: true
---

# Estratégia RMKT (NOVA — substitui modelo antigo)

## Modelo antigo (DEPRECADO — não fazer mais)

❌ Lead chegava → tag remarketing → se agendasse, tag agendado matava remarketing → se não, com 23h recebia oferta R$ 297 ainda na janela.

## Modelo NOVO (decisão Diego 2026-05-09)

### Cenário A — Cliente CLICOU em kit no E4 mas NÃO comprou

T+23h dispara re-oferta **específica do kit que cliente escolheu**, com **preço menor**:

| Tag adicionada (E4) | Re-oferta T+23h | Preço RMKT |
|---|---|---|
| `kit_5m` | RMKT 5 meses | [PENDENTE — Diego definir] |
| `kit_8m` | RMKT 8 meses | [PENDENTE] |
| `kit_12m` | RMKT 12 meses | [PENDENTE] |

**Lógica:** cliente já se interessou no kit, só precisa de empurrão. Preço menor + urgência.

### Cenário B — Cliente NÃO CLICOU em nenhum kit

Cascata genérica de remarketing:

| Timing | Mensagem |
|---|---|
| **T+48h** | RMKT genérico — projeção temporal + lembrar do problema |
| **T+72h** | RMKT genérico — depoimento real + senso de urgência |
| **T+7 dias** | RMKT genérico — última chance + benefício específico |

## Workflow trigger sugerido

### WF-RMKT-Especifico-Kit
- **Trigger:** Tag `kit_5m` OU `kit_8m` OU `kit_12m` adicionada **+** sem tag `cliente_pago` em 23h
- **Ação:** Branch baseado em qual tag → manda áudio + texto específicos do kit + nova oferta com preço menor

### WF-RMKT-Generico
- **Trigger:** Tag `passou_e3` adicionada **+** sem tag `kit_*` em 48h
- **Ação:** Cascata 48h/72h/7d com mensagens diferentes a cada toque

## Janela WhatsApp 24h — atenção crítica

- **T+23h** = **dentro** da janela 24h → mensagem livre (zero custo)
- **T+48h** em diante = **fora** da janela → precisa **template aprovado WhatsApp** (Meta cobra)

Templates aprovados a criar:
1. `rmkt_kit_5m_oferta_especial`
2. `rmkt_kit_8m_oferta_especial`
3. `rmkt_kit_12m_oferta_especial`
4. `rmkt_generico_lembrete_48h`
5. `rmkt_generico_urgencia_72h`
6. `rmkt_generico_ultima_chance_7d`

## Como Jaiane vai falar no RMKT

Tom mais direto e com urgência (não passivo). Exemplos:

### RMKT específico (ex: kit_8m)
```
$contact.firstname, separei uma condição especial pro Protocolo COMPLETO 8 MESES que você se interessou ontem 💕

Por hoje só, sai por R$ [preço RMKT]. Frete grátis e pagamento na entrega como sempre.

Bora fechar?
```

### RMKT genérico (T+48h)
```
$contact.firstname, sei que você passou por aqui há 2 dias procurando ajuda com [sintoma] 🌹

Deixa eu te perguntar: como você tá hoje? Os calorões/insônia/secura tão melhor ou pior?
```

→ Se cliente responder, voltar pro fluxo PT4 com o kit que faz mais sentido pro caso.

## Tag de exclusão importante

Lead que pagou (`cliente_pago = true`) **NUNCA** entra em RMKT. Workflow precisa filtrar.

Lead em raiva ou que pediu pra parar (`opt_out = true`) também **NUNCA** entra.
