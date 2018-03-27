Mass Payments
=============

Get All Mass Payment
--------------------

Get all mass payments from the user.

* `Get /mass/payments/` show all mass payment.

```json
{
   "data":[
      {
         "id":65,
         "status":"opened",
         "created_at":"2018-03-15T03:43:52.665Z",
         "formatted_value":"$ 0.00",
         "formatted_final_value":"R$ 300.00",
         "number_of_transaction":3
      },
      {
         "id":64,
         "status":"processed",
         "created_at":"2018-03-14T21:04:13.331Z",
         "formatted_value":"$ 95.02",
         "formatted_final_value":"R$ 300.00",
         "number_of_transaction":3
      },
      {
         "id":66,
         "status":"opened",
         "created_at":"2018-03-20T01:22:19.303Z",
         "formatted_value":"$ 0.00",
         "formatted_final_value":"R$ 300.00",
         "number_of_transaction":3
      },
      {
         "id":63,
         "status":"waiting_deposit",
         "created_at":"2018-03-14T21:01:41.031Z",
         "formatted_value":"$ 95.02",
         "formatted_final_value":"R$ 300.00",
         "number_of_transaction":3
      }
   ],
   "meta":{
      "code":200,
      "message":"success"
   }
}
```

Get Mass Payment
----------------

Get all information from a given mass payment.


* `GET /mass_payments/1/` shows mass payment.

```json
{
   "data":{
      "id":1,
      "status":"closed",
      "created_at":"2018-02-19T14:32:18.822Z",
      "formatted_value":"$ 8,407.00",
      "formatted_final_value":"R$ 25,419.98",
      "number_of_transaction":2
   },
   "meta":{
      "code":200,
      "message":"success"
   }
}
```

Get Mass Payment Status
-----------------------

Get the status of the transactions processed.

* `GET /mass_payments/1/status` will return the % of processed transactions in a mass payment.

```json
{
   "data":{
      "message":"Processed transactions: 80.0%"
   },
   "meta":{
      "code":200,
      "message":"success"
   }
}
```

Get Mass Payment Transactions
-----------------------------

Get the information of a given mass payment transactions

* `GET /mass_payments/1/transactions` will return all mass payment transactions.
* `GET /mass_payments/1/transactions?tid=1000` find and return the mass payment transaction that has id equals to 1000, if it exists.
* `GET /mass_payments/1/transactions?status=Failed` find and return the mass payment transactions that are in Faild status.
* `GET /mass_payments/1/transactions?status=Failed&tid=1000` find and return the mass payment transaction that is in Faild status and has id equals to 1000.


```json
{
   "data":[
      {
         "id":1047,
         "sender":null,
         "value":"200.0",
         "final_value":null,
         "subtotal":null,
         "savings":"34.44682",
         "current_total_savings":"59.085253917409",
         "market_rate":"3.2497",
         "service_fee":"3.2",
         "created_at":"2018-03-02T20:20:13.950Z",
         "formatted_value":"$200.00",
         "formatted_final_value":"R$ 0.00",
         "formatted_subtotal":"$0.00",
         "formatted_savings":"R$ 34.45",
         "formatted_current_total_savings":"R$ 59.09",
         "formatted_market_rate":"R$ 3.24970",
         "_links":null
      },
      {
         "id":1046,
         "sender":null,
         "value":"31.783465605523",
         "final_value":null,
         "subtotal":null,
         "savings":"5.474196593448",
         "current_total_savings":"30.112630510857",
         "market_rate":"3.2497",
         "service_fee":"3.2",
         "created_at":"2018-03-02T20:20:15.586Z",
         "formatted_value":"$31.78",
         "formatted_final_value":"R$ 0.00",
         "formatted_subtotal":"$0.00",
         "formatted_savings":"R$ 5.47",
         "formatted_current_total_savings":"R$ 30.11",
         "formatted_market_rate":"R$ 3.24970",
         "_links":null
      },
      {
         "id":1050,
         "sender":null,
         "value":"47.679593134139",
         "final_value":null,
         "subtotal":null,
         "savings":"8.212051811825",
         "current_total_savings":"32.850485729234",
         "market_rate":"3.2497",
         "service_fee":"3.2",
         "created_at":"2018-03-02T20:20:17.428Z",
         "formatted_value":"$47.68",
         "formatted_final_value":"R$ 0.00",
         "formatted_subtotal":"$0.00",
         "formatted_savings":"R$ 8.21",
         "formatted_current_total_savings":"R$ 32.85",
         "formatted_market_rate":"R$ 3.24970",
         "_links":null
      },
      {
         "id":1048,
         "sender":null,
         "value":"31.786395422759",
         "final_value":null,
         "subtotal":null,
         "savings":"5.474701207883",
         "current_total_savings":"30.113135125292",
         "market_rate":"3.2497",
         "service_fee":"3.2",
         "created_at":"2018-03-02T20:20:19.171Z",
         "formatted_value":"$31.79",
         "formatted_final_value":"R$ 0.00",
         "formatted_subtotal":"$0.00",
         "formatted_savings":"R$ 5.47",
         "formatted_current_total_savings":"R$ 30.11",
         "formatted_market_rate":"R$ 3.24970",
         "_links":null
      },
      {
         "id":1049,
         "sender":null,
         "value":"200.0",
         "final_value":null,
         "subtotal":null,
         "savings":"34.4659",
         "current_total_savings":"59.104333917409",
         "market_rate":"3.2515",
         "service_fee":"3.2",
         "created_at":"2018-03-02T20:13:01.751Z",
         "formatted_value":"$200.00",
         "formatted_final_value":"R$ 0.00",
         "formatted_subtotal":"$0.00",
         "formatted_savings":"R$ 34.47",
         "formatted_current_total_savings":"R$ 59.10",
         "formatted_market_rate":"R$ 3.25150",
         "_links":null
      }
   ],
   "meta":{
      "code":200,
      "message":"success"
   }
}
```

Create Mass Payment
-------------------

* `POST /mass_payments/new` will create a new mass payment.

The only parameter `transactions` is optional, which is a list of transactions to be created and attached to the new mass payment.

```json
{
   "transactions":[
      {
         "token":"JmNmH3Au5w5xgZw6eRKmUUm",
         "final_value":100.00,
         "currency":"USD",
         "invoice_url":"invoice/url/invoice.pdf"
      },
      {
         "token":"JmNm3AuL5w5xgZw6eRKmUUm",
         "final_value":100.00,
         "currency":"USD",
         "invoice_url":"invoice/url/invoice.pdf"
      },
      {
         "token":"JNmH3AuL5w5xgZw6eRKmUUm",
         "value":100.00,
         "currency":"USD",
         "invoice_url":"invoice/url/invoice.pdf"
      }
   ]
}
```

The parameter `value` and`final_value` are mutualy exclusive.

This will return `201 Created`, with a success message containing the new mass payment id number.


Close Mass Payment
------------------

* `PUT /mass_payments/1/close` will close the given mass payment.

When a mass payment is closed, no new transaction can't be added. All tranasctions are closed and currency, values, rates cannot be changed.


This will return `200 OK` if the close was a success, along with a success message.


Add Transactions
----------------

* `PUT /mass_payments/1/transactions` will add new transactions to a given mass payment.

The only parameter is `transactions`, which is a list of transactions to be created and attached to the mass payment.

```json
{
   "transactions":[
      {
         "token":"JmNmH3Au5w5xgZw6eRKmUUm",
         "final_value":100.00,
         "currency":"USD",
         "invoice_url":"invoice/url/invoice.pdf"
      },
      {
         "token":"JmNm3AuL5w5xgZw6eRKmUUm",
         "final_value":100.00,
         "currency":"USD",
         "invoice_url":"invoice/url/invoice.pdf"
      },
      {
         "token":"JNmH3AuL5w5xgZw6eRKmUUm",
         "value":100.00,
         "currency":"USD",
         "invoice_url":"invoice/url/invoice.pdf"
      }
   ]
}
```

The parameter `value` and`final_value` are mutualy exclusive.

This will return `200 OK` if the update was a success, along with a success message.
