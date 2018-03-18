The Husky API
====================

Husky has its own API. This is a REST-style API that uses JSON for serialization and OAuth 2 for authentication.

Base URL
----------------

Making a request
----------------

All URLs start with `https://app.husky.io/api/v1/`. **SSL only**. The path is prefixed with the API version. If we change the API in backward-incompatible ways, we'll bump the version marker and maintain stable support for the old URLs.

If you still in development, you shall use Husky sandbox environment. It's available under `https://test1.husky.io/api/v1/`. **SSL only**.

todo: request example.

That's all!


Authentication
--------------

todo: authentication guide.

No XML, just JSON
-----------------

We only support JSON for serialization of data. Our format is to have no root element and we use snake\_case to describe attribute keys. This means that you have to send `Content-Type: application/json; charset=utf-8` when you're POSTing or PUTing data into Husky.


Pagination
----------

Most collection APIs paginate their results. The first request returns up to
50 records. Check the next page for more results by adding `&page=2`, then
`&page=3`, and so on until you get an empty response.


Handling errors
---------------

If Husky is having trouble, you might see a 5xx error. `500` means that the app is entirely down, but you might also see `502 Bad Gateway`, `503 Service Unavailable`, or `504 Gateway Timeout`. It's your responsibility in all of these cases to retry your request later.


Rate limiting
-------------

You can perform up to 500 requests per 10 second period from the same IP address for the same account. If you exceed this limit, you'll get a [429 Too Many Requests](http://tools.ietf.org/html/draft-nottingham-http-new-status-02#section-4) response for subsequent requests. Check the `Retry-After` header to see how many seconds to wait before retrying the request.



API ready for use
-----------------

* [Destination Account](https://github.com/husky-misc/husky-api/blob/master/sections/destination_account.md)
* [Mass Payment](https://github.com/husky-misc/husky-api/blob/master/sections/mass_payment.md)
* [Banks](https://github.com/husky-misc/husky-api/blob/master/sections/banks.md)
* [Payment](https://github.com/husky-misc/husky-api/blob/master/sections/payment.md)
* [User](https://github.com/husky-misc/husky-api/blob/master/sections/user.md)
* [Session](https://github.com/husky-misc/husky-api/blob/master/sections/session.md)


Help us make it better
----------------------

Please tell us how we can make the API better. If you have a specific feature request or if you found a bug, please use GitHub issues. Fork these docs and send a pull request with improvements.

To talk with us and other developers about the API, [post a question on StackOverflow](http://stackoverflow.com/questions/ask) tagged `husky` or [open a support ticket](https://husky.io/support).
