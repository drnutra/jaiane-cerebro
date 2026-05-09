---
title: PT5 — Coleta de dados + Braip COD
publish: true
---

# PT5 — Coleta de dados + Agendamento Braip COD

Última etapa do funil. Cliente já escolheu kit. Jaiane coleta dados em UMA mensagem só e dispara pedido COD.

## Frase canônica de pedido (do dataset PT4 real)

```
💎 Agora vou precisar dessas informações para inserir seu pedido no sistema:

• Nome
• CPF (pra nota/transportadora)
• E-mail (caso tenha)
• CEP do seu endereço
• Rua
• Nº
• Bairro
• Cidade

Pode mandar tudo de uma vez 🌹
```

## Mapeamento campo → CF respond.io

| Cliente envia | Atualizar CF |
|---|---|
| Nome | `nome_completo` |
| CPF | `cpf` |
| E-mail | `email` |
| CEP | `cep` |
| Rua | `endereco_rua` |
| Número | `endereco_numero` |
| Bairro | `endereco_bairro` |
| Cidade | `endereco_cidade` |

## Quando todos os campos preenchidos

1. Tag `dados_completos`
2. Lifecycle `PEDINDO DADOS` → `AGENDADO`
3. Workflow externo dispara HTTP Request → n8n cria pedido COD Braip
4. Tag `enviado_braip`
5. Atribui vendedora humana (Round-Robin: Raíla / Wilane / Geane / Vitória) pra acompanhar entrega

## Mensagem de confirmação

```
💎 Parabéns $contact.firstname! Seu pedido tá fechado ✨

Kit: $kit_escolhido (cápsulas + gel)
Pagamento: na entrega via cartão (até 12x)
Prazo de entrega: 3 a 7 dias úteis

Vou continuar de olho aqui pra te ajudar quando o kit chegar 🌹
```

## Se cliente escolheu PIX antecipado

Resposta adicional após confirmação:
```
Como você escolheu PIX antecipado (frete express ⚡), segue a chave:

*PIX CNPJ:*
Empresa: DR NUTRA LTDA
Banco: ITAÚ UNIBANCO S.A
Chave: [VALIDAR COM DIEGO — não memorizar]

Pode mandar print do comprovante quando pagar 💕
```

⚠️ **PIX:** Jaiane NÃO confirma pagamento. Validação acontece via webhook Braip status 13. Se cliente disser "paguei", responder: "Anotado! Vou conferir aqui e te aviso assim que cair 🌹".

## Tratamento de dados parciais

Se cliente mandou só parte dos dados (ex: só nome + CEP):

```
Quase lá! Só faltam: $missing_fields. Pode me mandar pra fechar?
```

Onde `$missing_fields` é a lista de campos vazios.

## Se cliente errou CPF

Validação básica (11 dígitos):
- Se < 11 dígitos: "Esse CPF tá faltando alguns números, pode conferir?"
- Se inválido: handoff humano (vendedora valida via APIBrasil)

## Tempo máximo na PT5

Se cliente parou de responder em PT5 por > 30 min:
- Mensagem de retomada: "Oi $contact.firstname 🌹 ainda tá comigo? Faltava só [X campos] pra fechar."
- Se 23h sem resposta: lifecycle `ABANDONO_DADOS`, dispara workflow re-engager.
