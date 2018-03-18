Destination Account
===================

Get Destination Account
-----------------------

Get destination account information.

* `GET /destination_accounts/` show destination account.

```json
{
   "data":{
      "id":1,
      "bank_name":"341 - Banco Itaú S.A.",
      "account_owner_name":"John Doe",
      "account_owner_id":"xxx.xxx.xxx-xx",
      "account_number":"11111111",
      "account_digit":"1",
      "bank_branch_id":"0001",
      "bank_branch_digit":"1",
      "destination_country":"Brazil",
      "account_type":"Checking Account",
      "_links":{
         "self":"http://app.husky.io/api/v1/destination_accounts"
      }
   },
   "meta":{
      "code":200,
      "message":"success"
   }
}
```

Create Destination Account
--------------------------

Create a new destination account.


* `POST /destination_accounts/` will create destination account.


```json
{
   "account_owner_name":"John Dow",
   "account_owner_id":"xxx.xxx.xxx-x",
   "bank_name":"341 - Banco Itaú S.A.",
   "bank_branch_id":"0001",
   "bank_branch_digit":"1",
   "account_number":"11111111",
   "account_digit":"1",
   "destination_country":"Brazil",
   "account_type":"Checking Account"
}
```

The parameters `bank_branch_digit`, `account_digit` and `destination_country` are optional.
The parameter `account_type` must be one of the following values: `Checking Account` or `Savings Account`.

This will return `201 Created`, with a success message containing the newly created destination account as a json object.

Update Destination Account
--------------------------

Update a given destination account.

* `PUT /destination_accounts/1` will update a destination account information.

All parameters are optional.

```json
{
   "account_owner_name":"John Dow",
   "account_owner_id":"xxx.xxx.xxx-x",
   "bank_name":"341 - Banco Itaú S.A.",
   "bank_branch_id":"0001",
   "bank_branch_digit":"1",
   "account_number":"11111111",
   "account_digit":"1",
   "destination_country":"Brazil",
   "account_type":"Checking Account"
}
```

The parameter `account_type` must be one of the following values: `Checking Account` or `Savings Account`.

This will return `200 OK` if the update was a success, along with the destination account as a json object.
