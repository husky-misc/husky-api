User API
========

As operações usadas são as seguintes:

 1) Adicionar um novo usuário
 2) Adicionar documento
 3) Alterar idioma
 4) Consultar status da conta do usuário
 5) Consultar pendências de conformidades
 6) Consultar informações do usuário

1 - Adicionar um novo usuário
-----------------------------

Será utilizado o seguinte endpoint: `api/v1/users`

Exemplo:

```
curl -i -X POST "https://test1.husky.io/api/v1/users"
-H "Authorization: Bearer JmNmH3AuL5w5xgZw6eRKmUUm" -H "accept: application/json" -H "content-type: application/json" -d
'{
   "first_name":"John",
   "last_name":"Doe",
   "email":"john@doe.com",
   "cell_phone":"xxxx-xxxx",
   "password":"password",
   "password_confirmation":"password",
   "client_id": "e5d13d5e288d9881f4454e062567ecd3a369effb75aa665d1cdd9f5223ff3269",
   "secret_id": "dd15ac49f2dd0383c2e9973e16c132b1d897b6ba3783768dad5097cdaaf5ff49"
}'
```

Os parâmetros são o seguinet:

- `first_name`: nome do usuário
- `lat_name`: sobrenome do usuário
- `email`: email do usuário
- `cell_phone`: telefone celular do usuário
- `password`: senha do usuário
- `password_confirmation`: confirmação da senha do usuário
- `client_id`: client id da aplicação a qual o token do usuário será vinculado
- `secret_id`: secret id da aplicação a qual o token do usuário será vinculado

O retorno do exemplo acima será:

```json
{"data":{"uid":1,"email":"john@doe.com","first_name":"John","preferred_language":"en","token":"25cf6a9a85181f6bd4b598d4145e00602b1f4a7b86dc89ab2664bad40fa28f3f","_links":{"self":"https://test1.husky.io/api/v1/users/209"}},"meta":{"code":200,"message":"success"}}
```

2 - Adicionar documento
-----------------------

Será utilizado o seguinte endpoint: `api/v1/upload`

Exemplo:

```
curl -X POST "https://test1.husky.io/api/v1/upload" -H  "Authorization: Bearer JmNmH3AuL5w5xgZw6eRKmUUm" -H "content-type: multipart/form-data" -F "attachment=@/path/to/file" -F "class_attribute=id_doc"
```

O retorno do exemplo acima será:

```json
{"data":"{'id_doc_attribute': 'true'}","meta":{"code":200,"message":"success"}}
```

3 - Alterar idioma
------------------

Será utilizado o seguinte endpoint: `api/v1/users/preferred_language`

Exemplo:

```
curl -i -X PUT "https://test1.husky.io/api/v1/users/preferred_language" -H "Authorization: Bearer JmNmH3AuL5w5xgZw6eRKmUUm" -H "accept: application/json" -H "content-type: application/json" -d '{"preferred_language": "pt-br"}'
```

O retoro do exemplo acima será:

```json
{"data":"Preferred language successfully updated","meta":{"code":200,"message":"success"}}
```

4 - Consultar status da conta do usuário
-----------------------------------------

Será utilizado o seguinte endpoint: `api/v1/users/workflow`


Exemplo:

```
curl -i -X GET "https://test1.husy.io/api/v1/users/workflow" -H "Authorization: Bearer JmNmH3AuL5w5xgZw6eRKmUUm" -H "accept: application/json" -H "content-type: application/json"
```

O retorno do exemplo acima será:

```json
{"data":{"status":"draft","required_step":"execute_compliance","_links":{"self":"http1://test1.husky.io/api/v1/users/workflow","rel":"https://test1.husky.io/api/v1/compliance"}},"meta":{"code":200,"message":"success"}}
```

5 - Consultar pendências de conformidades
-----------------------------------------

Para consultar quais documentos já foram enviados e se eles foram rejeitados pelo sistema, será utilizado o seguinte endpoint: `api/v1/compliance`

Exemplo:

```
curl -i -X GET "https://test1.huky.io/api/v1/compliance" -H "Authorization: Bearer JmNmH3AuL5w5xgZw6eRKmUUm" -H "accept: application/json" -H "content-type: application/json"
```

O retorno do exemplo acima será:

```json
{"data":{"required_documents":[{"id":"id_doc","name":"Government Issued Picture ID","description":"Government Issued Picture ID","uploaded":true,"rejected":false,"_links":{"self":"https://test1.husky.io/api/v1/compliance/id_doc"}},{"id":"proof_of_address","name":"Proof of address","description":"Picture of Utility bill or Bank statement","uploaded":false,"rejected":false,"_links":{"self":"https://test1.husky.io/api/v1/compliance/proof_of_address"}}]},"meta":{"code":200,"message":"success"}}
```

6 - Consultar informações do usuário
------------------------------------

Será utilizado o seguinte endpoint: `api/v1/users/:id`

* `:id` é o id do usuário criado na opção (1)

Exemplo:

```
curl -i -X GET "https://test1.husky.io/api/v1/users/1" -H "Authorization: Bearer JmNmH3AuL5w5xgZw6eRKmUUm" -H "accept: application/json" -H "content-type: application/json"
```

O retorno do exemplo acima será:

```json
{"data":{"uid":1,"email":"john@doe.com","first_name":"John","preferred_language":"pt-br","_links":{"self":"https://test1.husky.io/api/v1/users/1"}},"meta":{"code":200,"message":"success"}}
```
