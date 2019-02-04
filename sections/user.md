Users
=====

Get User Information
--------------------

Get informaton of a user.

* `GET /users/1` shows information of a given user.

```json
{
   "data":{
      "uid":1,
      "email":"john@doe.com",
      "first_name":"John",
      "preferred_language":"en",
      "_links":{
         "self":"https://app.husky.io/api/v1/users/1"
      }
   },
   "meta":{
      "code":200,
      "message":"success"
   }
}
```

If the user does not exits a `404 Not Found` will be returned, along with an error message


Get User Workflow
-----------------

Get the status of a user's account.


* `GET /users/workflow/` shows user's account status and compliance requirements.

```json
{
   "data":{
      "status":"draft",
      "required_step":"execute_compliance",
      "_links":{
         "self":"https://app.husky.io/api/v1/users/workflow",
         "rel":"https://app.husky.io/api/v1/compliance"
      }
   },
   "meta":{
      "code":200,
      "message":"success"
   }
}
```

Get Compliance State
--------------------

Get user compliant state: the required documents, if they were succesfully uploaded and if they were rejected.

* `GET /compliance` will return compliant state of the user.

```json
{
   "data":{
      "required_documents":[
         {
            "id":"id_doc",
            "name":"Front of the Government Issued Picture ID",
            "description":"Front of the Government Issued Picture ID",
            "uploaded":false,
            "rejected":false,
            "rejected_reason":"none - id_doc not analyzed yet",
            "_links":{
               "self":"http://app.husky.io/api/v1/compliance/id_doc"
            }
         },
         {
            "id":"back_id_doc",
            "name":"Back of the Government Issued Picture ID",
            "description":"Back of the Government Issued Picture ID",
            "uploaded":false,
            "rejected":false,
            "rejected_reason":"none - id_doc not analyzed yet",
            "_links":{
               "self":"http://app.husky.io/api/v1/compliance/back_id_doc"
            }
         },
         {
            "id":"proof_of_address",
            "name":"Proof of address",
            "description":"Picture of Utility bill or Bank statement",
            "uploaded":false,
            "rejected":false,
            "rejected_reason":"none - proof_of_address not analyzed yet",
            "_links":{
               "self":"http://app.husky.io/api/v1/compliance/proof_of_address"
            }
         },
         {
            "id":"selfie",
            "name":"Selfie",
            "description":"Proof of life selfie",
            "uploaded":false,
            "rejected":false,
            "rejected_reason":"none - selfie facematch not analyzed yet",
            "_links":{
               "self":"http://app.husky.io/api/v1/compliance/selfie"
            }
         }
      ],
      "other_compliance_status":""
   },
   "meta":{
      "code":200,
      "message":"success"
   }
}
```

Create User
-----------

* `POST /users` will create a new user.

The following parameters are required:

```json
{
   "first_name":"John",
   "last_name":"Doe",
   "email":"john@doe.com",
   "cell_phone":"xxxx-xxxx",
   "password":"password",
   "password_confirmation":"password",
   "client_id": "client_id",
   "secret_id": "secret_id"
}
```

This will return `201 Created`, with a success message containing the newly created user information and access token.

Create User File Attachment
---------------------------

Upload a compliance file to a user.

* `POST /upload` will create a user attachment

```
curl -X POST "https://app.husky.io/api/v1/upload" -H  "Authorization: USER TOKEN" -H "content-type: multipart/form-data" -F "attachment=@/path/to/file" -F "class_attribute=proof_of_address"
```

The parameter `class_attribute` can be one of the followign: `id_doc`, `proof_of_address`, `social_security`, `tax_report` or `extra_files`.

This will return `201 Created`, with a success message.

Update User Preferred Language
------------------------------

The preferred language is English (en) by default.

* `PUT /users/preferred_language` will change the user preferred language.

```json
{
    "preferred_language": "pt-br"
}
```

This will return `200 OK`, along with a success message.
