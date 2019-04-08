---
title: Flowplayer API Reference

language_tabs:
  - shell
  - javascript

toc_footers:
  - <a href='https://flowplayer.com'>About Flowplayer</a>
  - <a href='https://flowplayer.com/pricing'>Sign up to use API's</a>

includes:
  - errors
  - analytics
  - livestreams
  - liveclips
  - livesources
  - players
  - playlists
  - user
  - workspace
  - organization

search: true
---

# Introduction

Welcome to Flowplayer API documentation!

This documentation covers all public API endpoints provided by our platform.

Code examples are provided in several languages. You can switch between languages by clicking the tab
headers.

The live API lives in https://hub.flowplayer.com

# Authentication

> Authenticate requests

```shell
# Just pass the JWT token in headers
curl https://hub.flowplayer.com/<endpoint> \
       -H "Authorization: Bearer <token>"
```

```javascript
// Obtain a authenticated copy of the client
const client = require('flowplayer-client')('<token>');
````

> Make sure to replace `<token>` with tthe token obtained from API


We use JWT to generate secure stateless tokens for accessing the API's.

Flowplayer API expects the token to be sent in `Authorization` header for every request.


## Obtaining authentication token

> Obtain a token

```shell
curl https://hub.flowplayer.com/auth/tokens -X POST \
       --data "email=<email>&password=<password>"
```

```javascript
const client = require('flowplayer-client');
try {
  let token = await client.login('<email>', '<passsword>').token;
} catch (e) {
  // Login failed
}
```

> The above command returns JSON structured like this:

```json
{
  "token": "<token>"
}
```

This endpoint is used to generate authentication tokens.

### HTTP Request

`POST https://hub.flowplayer.com/auth/tokens`

### Request Parameters

Parameter | Description
--------- | -------------------------------------
email     | Email associated with the platform
password  | Password associated with the platform

