Session API
===========

As operações usadas são as seguintes:

 1) Login
 2) Alterar senha
 3) Logout

1 - Login
----------

Para realizar o login de um usuário e pegar um novo token de acesso, será utilizado o seguinte endpoint: `api/v1/sessions`

Exemplo:

```
curl -i -X POST "https://test1.husky.io/api/v1/sessions" -H "accept: application/json" -H "content-type: application/json" -d
'{
   "email":"john@doe.com",
   "password":"password",
   "client_id":"e5d13d5e288d9881f4454e062567ecd3a369effb75aa665d1cdd9f5223ff3269",
   "secret_id":"dd15ac49f2dd0383c2e9973e16c132b1d897b6ba3783768dad5097cdaaf5ff49"
}'
```

Os parâmetros são o seguinet:

- `email`: email do usuário
- `password`: senha do usuário
- `password_confirmation`: confirmação da senha do usuário
- `client_id`: client id da aplicação a qual o token do usuário será vinculado
- `secret_id`: secret id da aplicação a qual o token do usuário será vinculado

O retorno do exemplo acima será:

```json
{"data":{"uid":208,"email":"john@doe.com","first_name":"John","preferred_language":"en","cell_phone":"xxxx-xxxx","token":"86473939a3c8b25e7d74404fb1022dd4501df0f82f41c8e5daf79c0fef5a8798","_links":{"self":"https://test1.husky.io/api/v1/users/208"}},"meta":{"code":200,"message":"success"}}
```

2 - Alterar senha
-----------------

Para alterar a senha duas operaçoes devem ser efetuadas:
 1) Pedir a alteração de senha
 2) Alterar a senha


#### 1 - Pedir a alteração de senha

Será utilizado o seguinte endpoint: `api/v1/sessions/recover`

Exemplo:

```
curl -i -X POST "https://test1.husky.io/api/v1/sessions/recover" -H "accept: application/json" -H "content-type: application/json" -d '{"email": "john@doe.com", "client_id": "e5d13d5e288d9881f4454e062567ecd3a369effb75aa665d1cdd9f5223ff3269", "secret_id": "dd15ac49f2dd0383c2e9973e16c132b1d897b6ba3783768dad5097cdaaf5ff49"}'

```

O retorno do exemplo acima será:

```json
{"data":{},"meta":{"code":200,"message":"If your email address exists in our database, you will receive a password recovery link at your email address in a few minutes."}}
```

Uma mensagem contendo as instruções para a mudança de senha será entregue para o email do usuário. Nele, conterá um link com o código de mudança de senha que será utilizado no passo seguinet.

#### 2 - Alterar a senha

Após o recebimento do email, a senha pode ser alterada utilizando o link na mensagem do email ou pelo seguinte endpoint: `api/v1/sessions/reset`

Exemplo:

```
curl -i -X POST "https://test1.husky.io/api/v1/sessions/reset" -H "accept: application/json" -H "content-type: application/json" -d '{"reset_password_token": "z6YyrPhfbTyuVqvExXqy", "password": "password", "password_confirmation": "password", "client_id": "e5d13d5e288d9881f4454e062567ecd3a369effb75aa665d1cdd9f5223ff3269", "secret_id": "dd15ac49f2dd0383c2e9973e16c132b1d897b6ba3783768dad5097cdaaf5ff49"}'
```

O retorno do exemplo acima será:

```json
{"data":{"uid":1,"email":"john@doe.com","first_name":"John","preferred_language":"en","cell_phone":"xxxx-xxxx","_links":{"self":"http://test1.husky.io/api/v1/users/1"}},"meta":{"code":200,"message":"success"}}
```

3 - Logout
----------

Para fazer o logout do usuário e destruir o código de acesso atual, será utilizado o seguinte endpoint: `api/v1/sessions/`

Exemplo:

```
curl -i -X DELETE "https://test1.husky.io/api/v1/sessions" -H "Authorization:Bearer 86473939a3c8b25e7d74404fb1022dd4501df0f82f41c8e5daf79c0fef5a8798"
```

O retoro do exemplo acima será:

```json
{"data":{},"meta":{"code":200,"message":"success"}}
```
