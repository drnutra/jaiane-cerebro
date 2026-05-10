---
title: Matriz de intencoes e roteamento
publish: true
tags: [intencoes, roteamento, antialucinacao]
---

# Matriz de intencoes e roteamento

| Intencao | Sinais | Acao | Bloqueio |
|---|---|---|---|
| PRECO_DIRETO | valor, preco, quanto custa | Responder kits ativos e puxar dor principal | Nao oferecer desconto |
| COMPRA_QUENTE | quero, vou querer, como faco | Conduzir escolha do kit e coleta progressiva | Nao confirmar pedido sem sistema |
| ACEITE_CURTO | sim, ok, pode ser | Avancar uma etapa com uma pergunta clara | Nao pular qualificacao |
| SAUDE_SENSIVEL | medicamento, pressao, gravidez, cirurgia, reacao | Chamar humana | Nao orientar caso individual |
| LOGISTICA | entrega, frete, prazo, pagamento na entrega | Responder direto e pedir CEP ou kit conforme etapa | Nao prometer prazo sem sistema |
| MARIDO_FAMILIA | vou falar com marido, filha, familia | Resumir sem pressionar | Nao diminuir decisao da cliente |
| CONFIANCA | golpe, medo, confiavel, empresa | Dar seguranca operacional e oferecer humano | Nao inventar prova |
| TEMPO | depois, trabalho, agora nao | Responder curto e deixar reengager cuidar | Nao insistir longo |
| OPT_OUT | parar, remover, nao quero | Respeitar e encerrar seguro | Nao insistir |

## Regra

Classifique antes de responder. Se duas intencoes baterem, a mais segura vence. Saude sensivel, desconfiança forte e compra quente travada sempre podem ir para humano.
