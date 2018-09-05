# Sitegroup

## Get Sitegroup (NOT IMPLEMENTED)

Endpoint for fetching infomation about one single Sitegroup

> Endpoint for fetching infomation about one single Sitegroup

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


## List Sitegroups 

Endpoint for fetching infomation about Sitegroups. This is only for Flowplayer Admins.

> Endpoint for fetching infomation about sitegroups on this platform.

```shell
curl "https://app.flowplayer.com/accounts/list"
```

```json
{
    "siteGroups": [
        {
            "id":"sitegroup_id_1",
            "name":"sitegroup_name",
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
siteGroups.id | Id for Sitegroup
siteGroups.name | Name for Sitegroup
siteGroups.created_at | Creation date for Sitegroup
siteGroups.https | If sitegroup videos support https (Should be removed)
siteGroups.distributor | If sitegroup can distribute videos to other Sitegroups
siteGroups.fp_legacy_user_id | If exists this is the user id for old Flowplayer.org

### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request

## Create Sitegroup (and everything needed for an account) (EXISTING, BUT TO REWRITE)

Endpoint for creating a Account. This endpoint will create Sitegroup, Site, User, Player configuration and demo videos needed when setting up an new account.

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

## Update Sitegroup (NOT IMPLEMENTED)

### HTTP Request



### Request parameters

Parameter | Description
--------- | -------------------------------------
TBD

### Response

Parameter | Description
--------- | -------------------------------------
TDB

## Delete SiteGroup 

Endpoint for deleting one single Sitegroup. This will in some cases (when enterprise) not delete the videos on the Sitegroup. 

### HTTP Request

`DELETE https://app.flowplayer.com/ovp/accounts/delete/{sitegroup_id}`

### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified SiteGroup is not found
