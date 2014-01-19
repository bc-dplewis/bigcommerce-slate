---
title: API Reference

language_tabs:
  - shell
  - ruby

toc_footers:
-  <span>&copy;</span> Bigcommerce
---

# Introduction

Welcome to the Bigcommerce Kitteh API.

You can use our API to access Bigcommerce Kitteh API endpoints, which can get information on various cats, kittehs, and breeds in our database.

We have language bindings in Shell &amp; Ruby.

# Authentication

> To authorize, use this code:

```ruby
require 'kitteh'

api = Bigcommerce::APIClient.authorize!('meowmeowmeow')
```

```python
import 'kitteh'

api = Bigcommerce.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

> Make sure to replace `meowmeowmeow` with your API key.

Bigcommerce uses API keys to allow access to the API. You can register a new Bigcommerce API key at our [developer portal](http://example.com/developers).

Bigcommerce expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace `meowmeowmeow` with your personal API key.
</aside>

# Kittehs

## Get All Kittehs

```ruby
require 'kitteh'

api = Bigcommerce::APIClient.authorize!('meowmeowmeow')
api.kittehs.get
```

```python
import 'kitteh'

api = Bigcommerce.authorize('meowmeowmeow')
api.kittehs.get()
```

```shell
curl "http://example.com/api/kittehs"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Isis",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittehs.

### HTTP Request

`GET http://example.com/kittehs`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittehs that have already been adopted.

<aside class="success">
Remember — a happy kitteh is an authenticated kitteh!
</aside>

## Get a Specific Kitteh

```ruby
require 'kitteh'

api = Bigcommerce::APIClient.authorize!('meowmeowmeow')
api.kittehs.get(2)
```

```python
import 'kitteh'

api = Bigcommerce.authorize('meowmeowmeow')
api.kittehs.get(2)
```

```shell
curl "http://example.com/api/kittehs/3"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Isis",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitteh.

<aside class="warning">If you're not using an administrator API key, note that some kittehs will return 403 Forbidden if they are hidden for admins only.</aside>

### HTTP Request

`GET http://example.com/kittehs/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the cat to retrieve

# Errors

The Bigcommerce API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request sucks
401 | Unauthorized -- Your API key is wrong
403 | Forbidden -- The kitteh requested is hidden for administrators only
404 | Not Found -- The specified kitteh could not be found
405 | Method Not Allowed -- You tried to access a kitteh with an invalid method
406 | Not Acceptable -- You requested a format that isn't json
410 | Gone -- The kitteh requested has been removed from our servers
418 | I'm a teapot
429 | Too Many Requests -- You're requesting too many kittehs! Slown down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarially offline for maintanance. Please try again later.
