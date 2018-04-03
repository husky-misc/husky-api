Mass Payment API
================

As operações usadas são as seguintes:

 1) Adicionar um mass payment
 2) Adicionar um pagamento em um mass payment já existente
 3) Finalizar um mass payment
 4) Consultar informações sobre mass payment
 5) Consultar status do mass payment
 6) Consultar pagamentos por status
 7) Consultar todos os mass payments

1 - Adicionar um mass payment
-----------------------------

Será utilizado o seguinte endpoint: `api/v1/mass_payments/new`

Exemplo:

```
curl -i -X POST "https://test1.husky.io/api/v1/mass_payments/new"
-H "Authorization: Bearer JmNmH3AuL5w5xgZw6eRKmUUm" -H "accept: application/json" -H "content-type: application/json" -d
'{
   "transactions":[
      {
         "token":"wiyXXTRNaWC8JV2h1oJneJ5a",
         "final_value":100.00,
         "currency":"USD",
         "invoice_url":"https://marketplace.canva.com/MACNHlOYjIo/2/0/thumbnail_large/canva-white-checkered-background-invoice-letterhead-MACNHlOYjIo.jpg"
      },
      {
         "token":"wiyXXTRNaWC8JV2h1oJneJ5a",
         "final_value":100.00,
         "currency":"USD",
         "invoice_url":"https://marketplace.canva.com/MACNHlOYjIo/2/0/thumbnail_large/canva-white-checkered-background-invoice-letterhead-MACNHlOYjIo.jpg"
      },
      {
         "token":"wiyXXTRNaWC8JV2h1oJneJ5a",
         "final_value":100.00,
         "currency":"USD",
         "invoice_url":"https://marketplace.canva.com/MACNHlOYjIo/2/0/thumbnail_large/canva-white-checkered-background-invoice-letterhead-MACNHlOYjIo.jpg"
      }
   ]
}'
```

Nesse exemplo, será criado um mass payment com 3 pagamentos. Os parâmetros de
cada pagamento é o seguinte:

- `token`: o token do usuário que deverá receber o pagamento
- `final_value`: o valor em real do pagament
- `currency`: qual a moeda para a conversão, no caso, USD
- `invoice_url`: uma URL contendo o invoice do pagameno

O retorno do exemplo acima será:

```
{"data":{"message":"Successfully created mass payment
#3", "mass_payment_id": "3"},"meta":{"code":200,"message":"success"}}
```

2 - Adicionar um pagamento em um mass payment já existente
----------------------------------------------------------

Será utilizado o seguinte endpoint: `api/v1/mass_payments/:id/transactions`

* `:id` é o número do mass payment criado na opção (1)


Exemplo:

```
curl -i -X PUT "https://test1.husky.io/api/v1/mass_payments/2/transactions" -H
"Authorization: Bearer JmNmH3AuL5w5xgZw6eRKmUUm" -H "accept: application/json" -H "content-type: application/json" -d
'{
   "transactions":[
      {
         "token":"wiyXXTRNaWC8JV2h1oJneJ5a",
         "final_value":100.00,
         "currency":"USD",
         "invoice_url":"https://marketplace.canva.com/MACNHlOYjIo/2/0/thumbnail_large/canva-white-checkered-background-invoice-letterhead-MACNHlOYjIo.jpg"
      },
      {
         "token":"wiyXXTRNaWC8JV2h1oJneJ5a",
         "final_value":100.00,
         "currency":"USD",
         "invoice_url":"https://marketplace.canva.com/MACNHlOYjIo/2/0/thumbnail_large/canva-white-checkered-background-invoice-letterhead-MACNHlOYjIo.jpg"
      },
      {
         "token":"wiyXXTRNaWC8JV2h1oJneJ5a",
         "final_value":100.00,
         "currency":"USD",
         "invoice_url":"https://marketplace.canva.com/MACNHlOYjIo/2/0/thumbnail_large/canva-white-checkered-background-invoice-letterhead-MACNHlOYjIo.jpg"
      }
   ]
}'
```

Nesse exemplo, 3 novos pagamentos serão adicionadas no mass payment #2. Os
parâmetros são os mesmos da opção (1)

O retorno do exemplo acima será:

```
{"data":{"message":"Successfully updated mass
payment"},"meta":{"code":200,"message":"success"}}
```

3 - Finalizar um mass payment
-----------------------------

Uma vez que todos o pagamentos foram incluidos no mass payment, é possível
finalizá-lo. Com isso, o câmbio atual será fixado e o valor final em dolar
calculado. É importante notar que após esse passo os valores não poderão ser
modificados.

Será utilizado o seguinte endpoint: `api/v1/mass_payments/:id/close`

* `:id` é o número do mass payment criado na opção (1)

Exemplo:

```
curl -i -X PUT "https://test1.husky.io/api/v1/mass_payments/2/close"  -H
"Authorization: Bearer JmNmH3AuL5w5xgZw6eRKmUUm" -H "accept: application/json" -H "content-type: application/json"
```

O retoro do exemplo acima será:

```
{"data":{"message":"Mass payment successfully
closed"},"meta":{"code":200,"message":"success"}}
```

4 - Consultar informações sobre mass payment
--------------------------------------------

Para consultar informações como: valor em real, valor em dolar, número de
pagametos e status do mass payment, o seguinte endpoint pode ser utilizado:
`api/v1/mass_payments/:id`

* `:id` é o número do mass payment criado na opção (1)

Exemplo:

```
curl -i -X GET "https://test1.husky.io/api/v1/mass_payments/2/"  -H
"Authorization: Bearer JmNmH3AuL5w5xgZw6eRKmUUm" -H "accept: application/json" -H "content-type: application/json"
```

O retorno do exemplo acima será:

```
{"data":{"id":2,"status":"closed","created_at":"2018-03-08T20:13:32.992Z","formatted_value":"$
171.43","formatted_final_value":"R$600.00","formatted_total_value":"$171.43", "formatted_total_final_value":"R$600.00",
"number_of_transaction":6},"meta":{"code":200,"message":"success"}}
```

5 - Consultar status do mass payment
------------------------------------

Para consultar a quantidade de pagamentos que foram realizados com sucesso, o
seguinte endpoint pode ser utilizado: `v1/mass_payments/:id/status`

* `:id` é o número do mass payment criado na opção (1)

Exemplo:

```
curl -i -X GET "https://test1.husky.io/api/v1/mass_payments/2/status"  -H
"Authorization: Bearer JmNmH3AuL5w5xgZw6eRKmUUm" -H "accept: application/json" -H "content-type: application/json"
```

O retorno do exemplo acima será:

```
{"data":{"message":"Processed transactions:
100.0%"},"meta":{"code":200,"message":"success"}}
```

6 - Consultar pagamentos por status
-----------------------------------

Caso seja necessário consultar pagamentos com um status específico, pode-se usar
o seguinte endpoint: `api/v1/mass_payments/:id/transactions?status=:status`

* `:id` é o número do mass payment criado na opção (1)
* `:status` é o status do pagamento. Valores possíveis: completed, failed, closed

Exemplo:

```
curl -i -X GET "https://test1.husky.io/api/v1/mass_payments/2/transactions?status=closed"  -H
"Authorization: Bearer JmNmH3AuL5w5xgZw6eRKmUUm" -H "accept: application/json" -H "content-type: application/json"
```

7 - Consultar todos os mass payments
------------------------------------

Para consultar todos os lotes criados por um usuário, pode-se usar o seguinte endpoint: `api/v1/mass_payments`

Exemplo:

```
curl -i -X GET "https://test1.husky.io/api/v1/mass_payments" -H "Authorization: Bearer JmNmH3AuL5w5xgZw6eRKmUUm" -H "accept: application/json" -H "content-type: application/json"
```

O retorno do exemplo acima será:

```
{"data":[{"id":65,"status":"opened","created_at":"2018-03-15T03:43:52.665Z","formatted_value":"$ 0.00","formatted_final_value":"R$ 300.00","number_of_transaction":3},{"id":64,"status":"processed","created_at":"2018-03-14T21:04:13.331Z","formatted_value":"$ 95.02","formatted_final_value":"R$ 300.00","number_of_transaction":3},{"id":66,"status":"opened","created_at":"2018-03-20T01:22:19.303Z","formatted_value":"$ 0.00","formatted_final_value":"R$ 300.00","number_of_transaction":3},{"id":63,"status":"waiting_deposit","created_at":"2018-03-14T21:01:41.031Z","formatted_value":"$ 95.02","formatted_final_value":"R$ 300.00","number_of_transaction":3}],"meta":{"code":200,"message":"success"}}
```

Mass Payment Flowchart
----------------------

![alt text](../pictures/mass_payment_flow.png?raw=true "Mass Payment")
