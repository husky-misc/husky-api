Payments API
============

As operações usadas são as seguintes:

 1) Consultar bancos disponíveis
 2) Consultar informações de dados bancarios do usuário
 3) Consultar pagamentos do usuário
 4) Consultar pagamento específico do usuário
 5) Enviar recibo de um pagamento para o usuário
 6) Criar informações de dados bancarios do usuário
 7) Alterar informações de dados bancarios do usuário

1 - Consultar bancos disponíveis
--------------------------------

Será utilizado o seguinte endpoint: `api/v1/banks`

Exemplo:

```
curl -i -X GET "https://test1.husky.io/api/v1/banks" -H "Authorization: Bearer JmNmH3AuL5w5xgZw6eRKmUUm" -H "accept: application/json" -H "content-type: application/json"
```

O retorno do exemplo acima será:

```json
{"data":["001 - Banco do Brasil S.A.","341 - Banco Itaú S.A.","033 - Banco Santander (Brasil) S.A.","356 - Banco Real S.A. (antigo)","652 - Itaú Unibanco Holding S.A.","237 - Banco Bradesco S.A.","745 - Banco Citibank S.A.","399 - HSBC Bank Brasil S.A. - Banco Múltiplo","104 - Caixa Econômica Federal","389 - Banco Mercantil do Brasil S.A.","453 - Banco Rural S.A.","422 - Banco Safra S.A.","633 - Banco Rendimento S.A.","246 - Banco ABC Brasil S.A.","025 - Banco Alfa S.A.","641 - Banco Alvorada S.A.","029 - Banco Banerj S.A.","038 - Banco Banestado S.A.","000 - Banco Bankpar S.A.","740 - Banco Barclays S.A.","107 - Banco BBM S.A.","031 - Banco Beg S.A.","096 - Banco BM&F de Serviços de Liquidação e Custódia S.A","318 - Banco BMG S.A.","752 - Banco BNP Paribas Brasil S.A.","248 - Banco Boavista Interatlântico S.A.","036 - Banco Bradesco BBI S.A.","204 - Banco Bradesco Cartões S.A.","225 - Banco Brascan S.A.","044 - Banco BVA S.A.","263 - Banco Cacique S.A.","473 - Banco Caixa Geral – Brasil S.A.","222 - Banco Calyon Brasil S.A.","040 - Banco Cargill S.A.","M08 - Banco Citicard S.A.","M19 - Banco CNH Capital S.A.","215 - Banco Comercial e de Investimento Sudameris S.A.","756 - Banco Cooperativo do Brasil S.A. – BANCOOB","748 - Banco Cooperativo Sicredi S.A.","505 - Banco Credit Suisse (Brasil) S.A.","229 - Banco Cruzeiro do Sul S.A.","003 - Banco da Amazônia S.A.","083-3 - Banco da China Brasil S.A.","707 - Banco Daycoval S.A.","M06 - Banco de Lage Landen Brasil S.A.","024 - Banco de Pernambuco S.A. – BANDEPE","456 - Banco de Tokyo-Mitsubishi UFJ Brasil S.A.","214 - Banco Dibens S.A.","047 - Banco do Estado de Sergipe S.A.","037 - Banco do Estado do Pará S.A.","041 - Banco do Estado do Rio Grande do Sul S.A.","004 - Banco do Nordeste do Brasil S.A.","265 - Banco Fator S.A.","M03 - Banco Fiat S.A.","224 - Banco Fibra S.A.","626 - Banco Ficsa S.A.","394 - Banco Finasa BMC S.A.","M18 - Banco Ford S.A.","233 - Banco GE Capital S.A.","734 - Banco Gerdau S.A.","M07 - Banco GMAC S.A.","612 - Banco Guanabara S.A.","M22 - Banco Honda S.A.","063 - Banco Ibi S.A. Banco Múltiplo","M11 - Banco IBM S.A.","604 - Banco Industrial do Brasil S.A.","320 - Banco Industrial e Comercial S.A.","653 - Banco Indusval S.A.","630 - Banco Intercap S.A.","249 - Banco Investcred Unibanco S.A.","184 - Banco Itaú BBA S.A.","479 - Banco ItaúBank S.A","M09 - Banco Itaucred Financiamentos S.A.","376 - Banco J. P. Morgan S.A.","074 - Banco J. Safra S.A.","217 - Banco John Deere S.A.","065 - Banco Lemon S.A.","600 - Banco Luso Brasileiro S.A.","755 - Banco Merrill Lynch de Investimentos S.A.","746 - Banco Modal S.A.","151 - Banco Nossa Caixa S.A.","735 - Banco Neon S.A","045 - Banco Opportunity S.A.","623 - Banco Panamericano S.A.","611 - Banco Paulista S.A.","643 - Banco Pine S.A.","638 - Banco Prosper S.A.","747 - Banco Rabobank International Brasil S.A.","M16 - Banco Rodobens S.A.","072 - Banco Rural Mais S.A.","250 - Banco Schahin S.A.","749 - Banco Simples S.A.","366 - Banco Société Générale Brasil S.A.","637 - Banco Sofisa S.A.","464 - Banco Sumitomo Mitsui Brasileiro S.A.","082-5 - Banco Topázio S.A.","M20 - Banco Toyota do Brasil S.A.","634 - Banco Triângulo S.A.","208 - Banco UBS Pactual S.A.","M14 - Banco Volkswagen S.A.","655 - Banco Votorantim S.A.","610 - Banco VR S.A.","370 - Banco WestLB do Brasil S.A.","021 - BANESTES S.A. Banco do Estado do Espírito Santo","719 - Banif-Banco Internacional do Funchal (Brasil)S.A.","073 - BB Banco Popular do Brasil S.A.","078 - BES Investimento do Brasil S.A.-Banco de Investimento","069 - BPN Brasil Banco Múltiplo S.A.","070 - BRB – Banco de Brasília S.A.","477 - Citibank N.A.","081-7 - Concórdia Banco S.A.","487 - Deutsche Bank S.A. - Banco Alemão","751 - Dresdner Bank Brasil S.A. – Banco Múltiplo","062 - Hipercard Banco Múltiplo S.A.","492 - ING Bank N.V.","488 - JPMorgan Chase Bank","409 - UNIBANCO – União de Bancos Brasileiros S.A.","230 - Unicard Banco Múltiplo S.A.","654 - Banco A.J.Renner S.A.","077-9 - Banco Intermedium S.A.","085 - VIACREDI - Cooperativa de Crédito Vale do Itajaí","260 - Nu Pagamentos S.A","121 - Banco Agiplan S.A.","212 - Banco Original S.A."],"meta":{"code":200,"message":"success"}}
```

2 - Consultar informações de dados bancarios do usuário
-------------------------------------------------------

Será utilizado o seguinte endpoint: `api/v1/destination_accounts`

Exemplo:

```
curl -i -X GET "https://test1.husky.io/api/v1/destination_accounts" -H "Authorization: Bearer JmNmH3AuL5w5xgZw6eRKmUUm" -H "accept: application/json" -H "content-type: application/json"
```

O retorno do exemplo acima será:

```json
{"data":{"id":1,"bank_name":"341 - Banco Itaú S.A.","account_owner_name":"John Dow","account_owner_id":"xxx.xxx.xxx-xx","account_number":"11111111","account_digit":"1","bank_branch_id":"0001","bank_branch_digit":"1","destination_country":"Brazil","account_type":"Checking Account","_links":{"self":"https://test1.husky.io/api/v1/destination_accounts"}},"meta":{"code":200,"message":"success"}}
```

3 - Consultar pagamentos do usuário
-----------------------------------

Será utilizado o seguinte endpoint: `api/v1/payments`

Exemplo:

```
curl -i -X GET "https://test1.husky.io/api/v1/payments" -H "Authorization: Bearer JmNmH3AuL5w5xgZw6eRKmUUm" -H "accept: application/json" -H "content-type: application/json"
```

O retoro do exemplo acima será:

```json
{"years":[{"year":2018,"payments":[{"id":1135,"currency":"USD","value":null,"formatted_value":null,"sender":null,"created_at":"2018-03-20T01:22:19.506Z","_links":[{"rel":"self","href":"https://test1.husky.io/api/v1/payments/1135"}]},{"id":1134,"currency":"USD","value":null,"formatted_value":null,"sender":null,"created_at":"2018-03-20T01:22:19.490Z","_links":[{"rel":"self","href":"https://test1.husky.io/api/v1/payments/1134"}]},{"id":1133,"currency":"USD","value":null,"formatted_value":null,"sender":null,"created_at":"2018-03-20T01:22:19.389Z","_links":[{"rel":"self","href":"https://test1.husky.io/api/v1/payments/1133"}]},{"id":1132,"currency":"USD","value":null,"formatted_value":null,"sender":null,"created_at":"2018-03-15T03:43:52.842Z","_links":[{"rel":"self","href":"https://test1.husky.io/api/v1/payments/1132"}]},{"id":1131,"currency":"USD","value":null,"formatted_value":null,"sender":null,"created_at":"2018-03-15T03:43:52.825Z","_links":[{"rel":"self","href":"https://test1.husky.io/api/v1/payments/1131"}]},{"id":1130,"currency":"USD","value":null,"formatted_value":null,"sender":null,"created_at":"2018-03-15T03:43:52.733Z","_links":[{"rel":"self","href":"https://test1.husky.io/api/v1/payments/1130"}]},{"id":1031,"currency":"USD","value":"31.68788698832","formatted_value":"$31.69","sender":null,"created_at":"2018-03-15T03:19:24.485Z","_links":[{"rel":"self","href":"https://test1.husky.io/api/v1/payments/1031"}]},{"id":1127,"currency":"USD","value":"31.67433713531","formatted_value":"$31.67","sender":null,"created_at":"2018-03-14T21:11:03.944Z","_links":[{"rel":"self","href":"https://test1.husky.io/api/v1/payments/1127"}]},{"id":1128,"currency":"USD","value":"31.67433713531","formatted_value":"$31.67","sender":null,"created_at":"2018-03-14T21:11:03.922Z","_links":[{"rel":"self","href":"https://test1.husky.io/api/v1/payments/1128"}]},{"id":1129,"currency":"USD","value":"31.67433713531","formatted_value":"$31.67","sender":null,"created_at":"2018-03-14T21:11:03.852Z","_links":[{"rel":"self","href":"https://test1.husky.io/api/v1/payments/1129"}]},{"id":1124,"currency":"USD","value":"31.67433713531","formatted_value":"$31.67","sender":null,"created_at":"2018-03-14T21:10:01.554Z","_links":[{"rel":"self","href":"https://test1.husky.io/api/v1/payments/1124"}]},{"id":1125,"currency":"USD","value":"31.67433713531","formatted_value":"$31.67","sender":null,"created_at":"2018-03-14T21:10:01.534Z","_links":[{"rel":"self","href":"https://test1.husky.io/api/v1/payments/1125"}]},{"id":1126,"currency":"USD","value":"31.67433713531","formatted_value":"$31.67","sender":null,"created_at":"2018-03-14T21:10:01.481Z","_links":[{"rel":"self","href":"https://test1.husky.io/api/v1/payments/1126"}]},{"id":1108,"currency":"USD","value":"31.67433713531","formatted_value":"$31.67","sender":null,"created_at":"2018-03-14T21:08:22.237Z","_links":[{"rel":"self","href":"https://test1.husky.io/api/v1/payments/1108"}]},{"id":1102,"currency":"USD","value":"53473.387272848089","formatted_value":"$53,473.39","sender":null,"created_at":"2018-03-13T20:52:04.709Z","_links":[{"rel":"self","href":"https://test1.husky.io/api/v1/payments/1102"}]},{"id":1101,"currency":"USD","value":null,"formatted_value":null,"sender":null,"created_at":"2018-03-13T20:49:41.675Z","_links":[{"rel":"self","href":"https://test1.husky.io/api/v1/payments/1101"}]}]}]}
```

4 - Consultar pagamento específico do usuário
---------------------------------------------

Será utilizado o seguinte endpoint: `api/v1/payments/:id`
* `:id`: é o identificador do pagamento do usuário que será consultado

Exemplo:

```
curl -i -X GET "https://test1.husky.io/api/v1/payments/1125" -H "Authorization: Bearer JmNmH3AuL5w5xgZw6eRKmUUm" -H "accept: application/json" -H "content-type: application/json"
```

O retorno do exemplo acima será:

```json
{"data":{"id":1125,"sender":null,"value":"31.67433713531","final_value":"100.0","subtotal":"30.66","savings":"5.475210080041","current_total_savings":"5.475210080041","market_rate":"3.2615","service_fee":"3.2","created_at":"2018-03-14T21:10:01.534Z","formatted_value":"$31.67","formatted_final_value":"R$ 100.00","formatted_subtotal":"$30.66","formatted_savings":"R$ 5.48","formatted_current_total_savings":"R$ 5.48","formatted_market_rate":"R$ 3.26150","_links":{"self":"https://test1.husky.io/api/v1/users/1125","send_receipt":"https://test1.husky.io/api/v1/payments/1125/send_receipt"}},"meta":{"code":200,"message":"success"}}
```

5 - Enviar recibo de um pagamento para o usuário
------------------------------------------------

Será utilizado o seguinte endpoint: `api/v1/payment/:id/send_receipt`
* `:id`: é o identificador do pagamento do usuário

Exemplo:

```
curl -i -X GET "https://test1.husky.io/api/v1/payments/1125/send_receipt" -H "Authorization: Bearer JmNmH3AuL5w5xgZw6eRKmUUm" -H "accept: application/json" -H "content-type: application/json"
```

O retorno do exemplo acima será:

```json
{"data":{"message":"PDF receipt sent"},"meta":{"code":200,"message":"success"}}
```

Um email contendo o recibo do pagamento em PDF será enviado para o email cadastrado do usuário.

6 - Criar informações de dados bancarios do usuário
---------------------------------------------------

Será utilizado o seguinte endpoint: `api/v1/destination_accounts`


Exemplo:

```
curl -i -X POST "https://test1.husky.io/api/v1/destination_accounts/" -H "Authorization: Bearer JmNmH3AuL5w5xgZw6eRKmUUm" -H "accept: application/json" -H "content-type: application/json" -d
'{
   "account_owner_name":"John Doe",
   "account_owner_id":"xxx.xxx.xxx-xx",
   "bank_name":"341 - Banco Itaú S.A.",
   "bank_branch_id":"0001",
   "bank_branch_digit":"9",
   "account_number":"11111111",
   "account_digit":"1",
   "destination_country":"Brazil",
   "account_type":"Checking Account"
}'
```

O retorno do exemplo acima será:

```json
{"data":{"id":176,"bank_name":"341 - Banco Itaú S.A.","account_owner_name":"John Doe","account_owner_id":"xxx.xxx.xxx-xx","account_number":"11111111","account_digit":"1","bank_branch_id":"0001","bank_branch_digit":"9","destination_country":"Brazil","account_type":"Checking Account","_links":{"self":"https://test1.husky.io/api/v1/destination_accounts"}},"meta":{"code":200,"message":"success"}}
```

7 - Alterar informações de dados bancarios do usuário
-----------------------------------------------------

Será utilizado o seguinte endpoint: `api/v1/destination_accounts/:id
* `:id`: identificador dos dados bancarios do usuário

Exemplo:

```
curl -i -X PUT "https://test1.husky.io/api/v1/destination_accounts/176" -H "Authorization: Bearer JmNmH3AuL5w5xgZw6eRKmUUm" -H "accept: application/json" -H "content-type: application/json" -d
'{
   "account_owner_name":"John Doe",
   "account_owner_id":"xxx.xxx.xxx-xx",
   "bank_name":"341 - Banco Itaú S.A.",
   "bank_branch_id":"0001",
   "bank_branch_digit":"1",
   "account_number":"11111111",
   "account_digit":"1",
   "destination_country":"Brazil",
   "account_type":"Checking Account"
}'
```

O retorno do exemplo acima será:

```json
{"data":{"id":176,"bank_name":"341 - Banco Itaú S.A.","account_owner_name":"John Doe","account_owner_id":"xxx.xxx.xxx-xx","account_number":"11111111","account_digit":"1","bank_branch_id":"0001","bank_branch_digit":"1","destination_country":"Brazil","account_type":"Checking Account","_links":{"self":"https://test1.husky.io/api/v1/destination_accounts"}},"meta":{"code":200,"message":"success"}}
```
