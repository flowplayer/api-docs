# Site

## Get Site (NOT IMPLEMENTED)

Endpoint for fetching infomation about one single Site

> Endpoint for fetching infomation about one single Site

```shell
curl "TBD"
```

```json
{
    TBD
}
```

### HTTP Request

`GET TBD`


### Request parameters

### Response

Parameter | Description
--------- | -------------------------------------

### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified Playlist is not found


## List Sites 

Endpoint for fetching infomation about Sites. This is only for Flowplayer Admins.

> Endpoint for fetching infomation about Sites on this platform.

```shell
curl "https://app.flowplayer.com/accounts/list"
```

```json
{
    "Sites": [
        {
            "id":"Site_id_1",
            "name":"Site_name",
            "created_at":"2018-01-01T12:00:00",
            "https":true,
            "distributor":false,
            "fp_legacy_user_id":"12312",
            "subscription":{
                "id":"sub_1",
                "period_starts_at":"2018-01-01T12:00:00",
                "period_ends_at":"2018-02-01T12:00:00",
                "state":"active"
            }
        }
    ]
}
```



### HTTP Request

`GET https://app.flowplayer.com/accounts/list`


### Request parameters

Parameter | Description
--------- | -------------------------------------
page        | `optional` - Page for response, default value is `0`.
pageSize        | `optional` - Page size for response, default value is `20`.
search | `optional` - Search term for filtering the response. Searches `name`.
sortBy | `optional` - Sorting column for the response, default value is `created_at`. Possible values: `created_at`, `name`.
sortOrder | `optional` - Sorting order for the response, default value is `desc`. Possible values `asc` and `desc`
filter | `optional` - TBD

### Response

Parameter | Description
--------- | -------------------------------------
Sites.id | Id for Site
Sites.name | Name for Site
Sites.created_at | Creation date for Site
Sites.https | If Site videos support https (Should be removed)
Sites.distributor | If Site can distribute videos to other Sites
Sites.fp_legacy_user_id | If exists this is the user id for old Flowplayer.org

### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request

## Create Site

Endpoint for creating a Account. This endpoint will create Site, Site, User, Player configuration and demo videos needed when setting up an new account.

> Endpoint for creating an account

```shell
curl "https://app.flowplayer.com/ovp/account/create"
```

```json
{
}
```

### HTTP Request

`POST https://app.flowplayer.com/ovp/account/create`


### Request parameters

Parameter | Description
--------- | -------------------------------------

### Response

Parameter | Description
--------- | -------------------------------------

## Update Site (NOT IMPLEMENTED)

### HTTP Request



### Request parameters

Parameter | Description
--------- | -------------------------------------
TBD

### Response

Parameter | Description
--------- | -------------------------------------
TDB

## Delete Site 

Endpoint for deleting one single Site. This will in some cases (when enterprise) not delete the videos on the Site. 

### HTTP Request

`DELETE https://app.flowplayer.com/ovp/accounts/delete/{Site_id}`

### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified Site is not found
