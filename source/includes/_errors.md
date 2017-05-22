# Errors

> Example of an invalid request

```shell
# Missing request body
curl -X POST https://api.flowplayer.org/auth/tokens
```

```javascript
const client = require('flowplayer-client');
client.login(); // Missing email and password
```

> The service will respond with `HTTP/1.1 400 Bad Request`


```json
{
   "message" : "Input validation failed",
   "errors" : [
      {
         "message" : "\"email\" is required",
         "context" : {
            "key" : "email"
         },
         "type" : "any.required",
         "path" : "email"
      }
   ]
}
```

If the request cannot be fullfilled the HTTP request will have an error status code.

The codes used by the API are:

Error Code | Meaning
---------- | -------
400 | Bad Request -- Request has malformed input, clarification will be given in `message` and `errors` properties
401 | Unauthorized -- Access token in `Authorization` header is either missing or invalid
404 | Not Found -- Endpoint or resource not found
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.


