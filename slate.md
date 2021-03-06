---
title: API Reference
  

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='http://github.com/waranti/slate'>Documentation Powered by WarantiSlate</a>

includes:
  - errors

search: true
---




# Introduction

Welcome to the Waranti API! You can use our API to access Kittn API endpoints, which can get information on various cats, waranti, and breeds in our database.

We have language bindings in Shell, Ruby, and Python! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](http://github.com/waranti/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

> To authorize, use this code:


require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')


> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Waranti

## Get All Waranti

require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.waranti.get


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

This endpoint retrieves all waranti.

### HTTP Request

`GET http://example.com/api/waranti`

### Query Parameters

| Parameter | Default | Description |
| ---- | ---- | ---- |
| include_cats | false | If set to true, the result will also include cats. |
| available | true | If set to false, the result will include waranti that have already been adopted. |

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten


require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.waranti.get(2)


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

This endpoint retrieves a specific kitten.

<aside class="warning">If you're not using an administrator API key, note that some waranti will return 403 Forbidden if they are hidden for admins only.</aside>

### HTTP Request

`GET http://example.com/waranti/<ID>`

### URL Parameters

Parameter | Description
---- | ----
ID | The ID of the kitten to retrieve

