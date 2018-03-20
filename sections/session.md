Sessions
========

Create User Session
-------------------

Authenticate user and get access token.

* `POST /sessions` will authenticate a user.

```json
{
    "email": "john@doe.com",
    "password": "password"
}
```

This will return `201 Created` if the email/password combination matches, along with the user access token

Create Password Recovery Token
------------------------------

Send a password recovery token with instructions via email.


* `POST /sessions/recover` request password recovery to a user.

```json
{
    "email": "john@doe.com"
}
```

This will return `201 Created`. An mail with a password recovery token will be sent to the email provided.

Create New Password
-------------------

Create a new password to an user.

* `POST /sessions/reset` will reset the user password.

```json
{
    "reset_password_token": "password_token",
    "password": "password",
    "password_confirmation": "password"
}
```

The `reset_password_token` is the password recovery token generated by `Create Password Recovery Token`.

Thi will return `201 Created`, along with a success message.

Delete Session
--------------

Logout user and remove access token.

* `DELETE /sessions` will delete user session.

This will return `200 OK`, with a success message.