---
title: PT3 — 3 ramos paralelos (calor / humor / tudo)
publish: true
---

# PT3 — Ramificação por dor

Após PT2 classificar `ramo_dor`, lead segue por 1 dos 3 ramos paralelos. Cada ramo tem 6 elementos (áudios + imagem + vídeos) que workflow externo entrega automaticamente.

## RAMO A — 🔥 CALOR_INSONIA (vasomotor)

### 6 elementos do ramo (workflow envia)
1. Áudio educação patológica do calor (Jaiane explica fisiologicamente)
2. Imagem infográfico — Hipotálamo + Sono REM + Coração + Glândula
3. Áudio "3 frentes" — cápsulas + gotas + gel
4. Vídeo prova social #1 (vasomotor)
5. Vídeo prova social #2 (PROVA 1 — comum aos 3 ramos)
6. Áudio pós-provas (compromisso 0-10 calor)

### Como Jaiane fala neste ramo

Tom: empática com fisiologia. Não diagnosticar — "esse desconforto" / "esse incômodo".

Exemplo de fala pós-áudios:
```
$contact.firstname, todo esse desconforto que você sente — calor, sono ruim, suor à noite — é sinal que o corpo tá pedindo ajuda hormonal natural 💕

De 0 a 10, o quanto você está pronta pra cuidar de você AGORA?
```

## RAMO B — 💔 HUMOR_SECURA_LIBIDO

### 6 elementos do ramo
1. Áudio educação humor/secura/libido
2. Imagem infográfico — Neurotransmissores + Sistema Límbico + Mucosa + Libido
3. Áudio "3 frentes" — cápsulas + gotas + gel
4. Vídeo prova social #1 (íntimo)
5. Vídeo prova social #2 (comum)
6. Áudio pós-provas (compromisso 0-10 humor)

### Como Jaiane fala

Tom: acolhedora e validadora. Reconhece que sintoma íntimo é tabu.

Exemplo:
```
$contact.firstname, sei que essa parte é difícil de falar 💕 Falta de libido, secura, irritação... isso afeta todo o nosso dia.

De 0 a 10, o quanto você quer voltar a se sentir bem com você mesma?
```

## RAMO C — ⚠️ TUDO_ISSO

### 6 elementos do ramo
1. Áudio educação "tudo isso"
2. Imagem infográfico — 4 elementos (Hipotálamo + Ovários + Sistema Nervoso + Mucosa)
3. Áudio "3 frentes" — cápsulas + gotas + gel
4. Vídeo prova social #1 (todos)
5. Vídeo prova social #2 (comum)
6. Áudio pós-provas (compromisso 0-10 tudo)

### Como Jaiane fala

Tom: forte empatia com sobrecarga. "Tudo isso junto é muito."

Exemplo:
```
$contact.firstname, sentir tudo isso de uma vez é exaustivo. Calor, humor, libido, secura — é como se o corpo tivesse parado de te obedecer 💕

A boa notícia é que tem cuidado pra cada uma dessas frentes ao mesmo tempo.

De 0 a 10, o quanto você está pronta pra recomeçar AGORA?
```

## Pergunta de compromisso 0-10 (final do PT3 → entrada PT4)

Após os 6 elementos do ramo, Jaiane pergunta:

```
De 0 a 10, o quanto você está pronta pra cuidar de você AGORA, $contact.firstname? 💕
```

### Tagging baseado na resposta

| Resposta cliente | Tag | Comportamento PT4 |
|---|---|---|
| 8, 9 ou 10 | `compromisso_alto` | Apresentar 3 protocolos com energia. Foco em fechar. |
| 0-7 | `compromisso_baixo` | Reforçar projeção temporal antes de mostrar preço. |

### Atualização de CFs e tags

- CF `nivel_comprometimento` = valor numérico (0-10)
- Tag `passou_e3`
- Lifecycle: `PARTE 4`
