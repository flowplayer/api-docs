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


## List Workspaces in Organization

Endpoint for fetching all workspaces in a Organization. This is available for all users with Admin access on that Organization. 

> Endpoint for fetching workspaces with matching `flowplayer`

```shell
curl 'https://api.flowplayer.com/ovp/organizations/<ORGANIZATION_ID>/workspaces?query={"sort":{"by":"created_at","order","asc"},"search":"flowplayer","filters":[{"key":"workspace","value":["WORKSPACE_ID_1","WORKSPACE_ID_2"]}]}'
```

```javascript
 'https://api.flowplayer.com/ovp/organizations/<ORGANIZATION_ID>/workspaces?query={"sort":{"by":"created_at","order","asc"},"search":"flowplayer","filters":[{"key":"workspace","value":["WORKSPACE_ID_1","WORKSPACE_ID_2"]}]}'
```

```json
{
   {
    "query": {
        "page": 0,
        "page_size": 20,
        "search": "flowplayer",
        "sort": {
            "by": "created_at",
            "order": "ASC"
        },
        "filters": []
    },
    "total_count": 1639,
    "total_count_in_search": 1,
    "page": 0,
    "page_size": 20,
    "total_pages": 1,
    "search_term": "flowplayer",
    "assets": [
        {
            "id": "<WORKSPACE_ID_1>",
            "name": "flowplayer workspace",
            "default_category_id": "<CATEGORY_ID_1>",
            "url": "https://flowplayer.com",
            "sitegroup_id": "<ORGANIZATION_ID>",
            "delete_on_unpublish": false,
            "keep_original": false,
            "time_zone": "(GMT+01:00) Stockholm",
            "created_at": "2015-12-07T14:05:53+0100"
        }
    ]
}
```



### HTTP Request

`GET https://app.flowplayer.com/organizations/<ORGANIZATION_ID>/workspaces`


### Request parameters

Parameter | Description
--------- | -------------------------------------
page        | `optional` - Page for response, default value is `0`.
page_size        | `optional` - Page size for response, default value is `20`.
search | `optional` - Search term for filtering the response. Searches `name`.
sort.by | `optional` - Sorting column for the response, default value is `created_at`. Possible values: `created_at`, `name`.
sort.order | `optional` - Sorting order for the response, default value is `desc`. Possible values `asc` and `desc`
filter | `optional` - No filters available are currently available.

### Response

Parameter | Description
--------- | -------------------------------------
TBD

### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request

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
