---
title: PT2 — Classificação áudio livre
publish: true
---

# PT2 — Classificação do áudio livre

Cliente respondeu PT1 com áudio livre descrevendo sintomas. Jaiane classifica em 1 de 3 ramos.

## Sequência E2

1. Áudio Jaiane qualificação (~2min) — pergunta sobre tempo de sintoma e medicamento
2. Texto: "Me fala em áudio a quanto tempo você está sofrendo com esse problema e se você está tomando algum medicamento?"
3. **Cliente responde em áudio livre** ← ponto de classificação
4. Jaiane escuta + classifica em 1 dos 3 ramos
5. Atualiza `ramo_dor` + adiciona tag → vai pra PT3

## Mapeamento dor → ramo

### 🔥 RAMO A — CALOR_INSONIA (vasomotor)

Palavras-chave: `calor`, `calorão`, `calorões`, `ondas de calor`, `fogachos`, `insônia`, `não consigo dormir`, `sono ruim`, `acordo suando`, `suando à noite`

Frases reais que entram aqui:
- "Tenho muitos calores"
- "Não durmo direito"
- "Acordo encharcada de suor"
- "Ondas de calor durante o dia"

→ Tag: `dor_calor` · CF: `ramo_dor` = `calor_insonia`

### 💔 RAMO B — HUMOR_SECURA_LIBIDO

Palavras-chave: `humor`, `irritada`, `ansiosa`, `triste`, `deprimida`, `secura`, `ressecada`, `vagina seca`, `libido`, `desejo`, `sem vontade`, `sem libido`, `falta de desejo`, `frieza`

Frases reais:
- "Falta de libido total"
- "Tô muito irritada com tudo"
- "Sem vontade nenhuma"
- "Vagina seca, dor na relação"

→ Tag: `dor_humor` · CF: `ramo_dor` = `humor_secura_libido`

### ⚠️ RAMO C — TUDO_ISSO

Palavras-chave: `tudo`, `tudo isso`, `todos os sintomas`, `tudo que você falou`, `vários`, `muita coisa`, `não sei nem por onde começar`

Frases reais:
- "Sinto tudo isso"
- "Todos os sintomas que você falou"
- "Tô sentindo tudo de uma vez"
- "Várias coisas, não sei explicar"

→ Tag: `dor_tudo` · CF: `ramo_dor` = `tudo_isso`

## Quando classificação é ambígua

Se cliente mencionar 2 ramos com igual peso, jogar em **TUDO_ISSO** por padrão (oferta protocolo completo de 8 meses serve melhor pra múltiplos sintomas).

Se cliente respondeu de forma vaga ("não sei", "muita coisa"), perguntar uma vez: "Me conta a UMA coisa que mais te atrapalha hoje, $contact.firstname 💕". Se vier vago de novo → TUDO_ISSO.

## Idade declarada

Capturar `idade_declarada` quando cliente mencionar (durante áudio livre):
- "Tenho 57 anos"
- "Tenho 45"
- "Sou de 1960"

Se idade < 40 OU > 65: tag `fora_icp_idade`, lifecycle Sem Resposta, encerrar com:

```
Que carinho de você ter chegado, $contact.firstname 🌹 Mas esse cuidado foi feito especialmente pra mulheres na faixa da menopausa (40-65 aninhos). Vou deixar registrado pra gente conversar lá na frente se mudar 💕
```
