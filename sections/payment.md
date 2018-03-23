Payments
========

Get Payments
------------

Get all payments of a user.


* `GET /payments/` shows all payments.

```json
{
   "years":[
      {
         "year":2018,
         "payments":[
            {
               "id":1128,
               "currency":"USD",
               "value":"31.67433713531",
               "formatted_value":"$31.67",
               "sender":"Husky",
               "created_at":"2018-03-14T21:11:03.922Z",
               "_links":[
                  {
                     "rel":"self",
                     "href":"http://app.husky.io/api/v1/payments/1128"
                  }
               ]
            },
            {
               "id":1031,
               "currency":"USD",
               "value":"31.68788698832",
               "formatted_value":"$31.69",
               "sender":"Husky",
               "created_at":"2018-03-15T03:19:24.485Z",
               "_links":[
                  {
                     "rel":"self",
                     "href":"http://app.husky.io/api/v1/payments/1031"
                  }
               ]
            }
         ]
      }
   ]
}
```

Search Payment
--------------

Get a specific payment of a user.

* `GET /payments/1/` will return the payment of id 1 for the user, if it exists.

```json
{
   "data":{
      "id":1031,
      "sender":null,
      "value":"31.68788698832",
      "final_value":"100.0",
      "subtotal":"30.67",
      "savings":"5.475201059643",
      "current_total_savings":"10.950411139684",
      "market_rate":"3.2601",
      "service_fee":"3.2",
      "created_at":"2018-03-15T03:19:24.485Z",
      "formatted_value":"$31.69",
      "formatted_final_value":"R$ 100.00",
      "formatted_subtotal":"$30.67",
      "formatted_savings":"R$ 5.48",
      "formatted_current_total_savings":"R$ 10.95",
      "formatted_market_rate":"R$ 3.26010",
      "_links":{
         "self":"http://app.husky.io/api/v1/users/1031",
         "send_receipt":"http://app.husky.io/api/v1/payments/1031/send_receipt"
      }
   },
   "meta":{
      "code":200,
      "message":"success"
   }
}
```

In case the payment does not exists, a `404 Not Found` will be returned, along with an error message.

Send receipt of a payment
-------------------------

Send to the user a pdf receipt of a given payment.

* `GET /payments/1/send_receipt/` will email the pdf receipt of a given payment to the user, if it exists.

```json
{
   "data":{
      "message":"PDF receipt sent"
   },
   "meta":{
      "code":200,
      "message":"success"
   }
}
```

In case the payment does not exists, a `404 Not Found` will be returned, along with an error message.
