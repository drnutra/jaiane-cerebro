---
title: Pós-venda — pré-entrega + cobrança soft
publish: true
---

# Pós-venda

Após pedido criado no Braip (lifecycle `AGENDADO`), Jaiane mantém vínculo até pagamento confirmado.

## Etapas do pós-venda

```
AGENDADO (pedido criado)
   ↓
Pré-entrega (acompanhamento diário)
   ↓
SAIU PRA ENTREGA / EM TRÂNSITO (mudança status Braip)
   ↓
ENTREGUE / AGUARDANDO RETIRADA
   ↓
Cobrança soft → cliente paga → COBRANÇA PAGA / PAGO ✅
```

## Mensagens de pré-entrega (entre AGENDADO e SAIU PRA ENTREGA)

**Objetivo:** manter cliente ativa, não deixar esfriar entre pedido e entrega (3-7 dias).

### Dia +1 após pedido
```
$contact.firstname, seu pedido foi confirmado e tá sendo separado pra envio 🌹

Quando sair pra entrega eu te aviso. Tá tudo certinho com você?
```

### Dia +3 (sem mudança status)
```
Oi $contact.firstname 💕 Passando pra avisar que seu pedido tá em rota pra sua cidade. Em breve você recebe.

Te aviso assim que sair pra entrega ✨
```

### Dia +5 (se Braip atualizou pra "saiu pra entrega")
```
$contact.firstname, seu pedido SAIU pra entrega hoje 🌹

Se possível, deixa alguém em casa hoje pra receber, tá bem? O entregador leva o kit + a maquininha de cartão pra pagamento na entrega.
```

## Cobrança soft (pós-entrega)

Trigger: lifecycle muda pra `ENTREGUE` (via webhook Braip).

### Mensagem 1 — confirmação de entrega
```
$contact.firstname, vi aqui que seu kit chegou! 💕

Como foi a entrega? Recebeu certinho? Vou continuar de olho aqui pra te orientar quando começar o uso 🌹
```

### Se cliente confirmou entrega mas pagamento NÃO caiu
24h depois da entrega:
```
$contact.firstname, tudo bem com você?

Vi que o kit foi entregue ontem mas a confirmação do pagamento ainda não caiu aqui no nosso sistema. Pode ser que tenha demorado um pouquinho pra processar — tá tudo certo de você lado?
```

### Cobrança 48h após entrega sem pagamento
```
$contact.firstname, te chamando aqui pra confirmar:

Você recebeu o kit + a maquininha do entregador? O pagamento na entrega tem que ser feito direto na hora com o entregador. Se aconteceu algum problema, me avisa pra eu resolver pra você 🌹
```

→ Se cliente disser que pagou: validar via Braip (status 13). Se disser que não pagou: handoff cobradora humana (Rayane ou Maria).

## Atribuição da cobradora

Workflow externo atribui cobradora baseado em qual vendedora pegou o lead:

| Vendedora original | Cobradora |
|---|---|
| Raíla | Rayane |
| Wilane | Rayane |
| Geane | Maria |
| Vitória | Maria |

CF `cobradora_destino` = `EQUIPE RAYANE` ou `EQUIPE MARIA`.

## Limites duros

- ⚠️ Jaiane **NUNCA confirma pagamento sozinha** — só webhook Braip status 13 confirma
- ⚠️ Se cliente disser "paguei" e Braip não confirmou: "Anotado! Vou conferir aqui e te aviso assim que cair 🌹"
- ⚠️ Se Braip não confirmou em 5 dias: handoff cobradora pra ligar
- ⚠️ Jaiane **NUNCA inventa** cupom de desconto pra cliente que disse "tô sem dinheiro pra pagar"

## Recompra (após PAGO)

Quando cliente termina o kit (estimativa baseada em tempo de uso):
- 3 meses após PAGO (kit 5M finalizando) → mensagem de recompra
- 5 meses após PAGO (kit 8M finalizando) → mensagem de recompra
- 9 meses após PAGO (kit 12M finalizando) → mensagem de recompra

### Mensagem de recompra
```
$contact.firstname! 💕

Tá quase acabando seu kit, né? Pra continuar o protocolo sem interrupção, posso já fechar o próximo pra você?

A gente recomenda o de 8 meses pra manutenção (R$627), tem o melhor custo-benefício 🌹
```

CF `tem_pagado_antes` = true marca esse contato como recompra. Workflow RMKT precisa filtrar.
