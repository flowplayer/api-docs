# Livesources

## List Livesources

List Livesources on a Workspace

> List Livesources on a Workspace


```shell
curl "https://api.flowplayer.com/ovp/workspaces/:workspace_id/livesources"
```

```json
{
    "total_count": 2,
    "total_count_in_search": 2,
    "page": 0,
    "page_size": 20,
    "total_pages": 1,
    "search_term": "",
    "assets": [
        {
            "id": "73ff9d88-3ed7-48ec-81c3-0d99aeb1a333",
            "name": "Studio",
            "description": "Configured on our Studio computer",
            "stream_name": "32De23",
            "ingest_url": "rtmp://sample.input.flowplayer.com:1935/live",
            "type":"STREAM",
            "owner":{
              "id":"workspace_id_1",
              "name":"workspace 1"
            }
        },
        {
            "id": "764335ee-bd56-4f1f-b610-f703ddaf6545",
            "name": "iPhone",
            "description": "In iPhone app",
            "stream_name": "Rpdo32",
            "ingest_url": "rtmp://sample.input.flowplayer.com:1935/live",
            "type":"REMOTE",
            "remote_hls_url":"https://flowplayer.com/awesome_livestream.m3u8",
            "owner":{
              "id":"workspace_id_2",
              "name":"workspace 2"
            }
        }
    ]
}
```

### HTTP Request

`GET https://api.flowplayer.com/ovp/workspaces/:workspace_id/livesources`

### Request parameters

Parameter | Description
--------- | -------------------------------------
page        | `optional` - Page for response, default value is `0`.
page_size        | `optional` - Page size for response, default value is `20`.
search | `optional` - Search term for filtering the response. Searches `name`.
sort_by | `optional` - Sorting column for the response, default value is `name`. Possible values: `name`.
sort_order | `optional` - Sorting order for the response, default value is `desc`. Possible values `asc` and `desc`
filters | It's possible to use multiple different filters in the query. The different filter keys are listed below.
key.type | `optional` - Values should be an array of different Livesource types. Allowed values are `REMOTE`,`STREAM`.
key.only_own | `optional` - If only Livesources which the current Workspace as owner should be displayed or if all Livesources the Workspace have access to should be displayed.

### Response

Parameter | Description
--------- | -------------------------------------
assets[].id | Id for Livesource
assets[].name | Name for Livesource
assets[].description | Description for Livesource
assets[].stream_name | Identifier for the Livesource on our livestreaming servers. This shall be used in your broadcast software to identify this Livesource.
assets[].ingest_url | Url to our livestreaming servers. This shall be used in your broadcast software to send your input to the correct livestreaming server for this Livesource.
assets[].stream_name | Identifier for the Livesource on our livestreaming servers. This shall be used in your broadcast software to identify this Livesource.
assets[].type | Type of live source. Currently there are two types of Livesources, `STREAM` and `REMOTE`.
assets[].remote_hls_url | Only exists on Livesources with `REMOTE`-type. This url is used by the enduser to view the stream in the player.
assets[].type | Type of live source. Currently there are two types of Livesources, `STREAM` and `REMOTE`.
assets[].owner.id | Workspace Id for the workspace that owns the Livesource.
assets[].owner.name | Workspace name for the workspace that owns the Livesource.

### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified Workspace is not found


## Get Livesource

Endpoint for fetching one Livesource

> Endpoint for fetching one Livesource

```shell
curl "https://api.flowplayer.com/ovp/workspaces/:workspace_id/livesources/:livesource_id"
```

```json
{
    "id": "951ba340-2949-4299-9b55-5d33b3bc9a5e",
    "name": "Flowplayer Livesource",
    "description": "On Office computer",
    "stream_name": "8fbpE5iA",
    "ingest_url": "rtmp://sample.input.flowplayer.com:1935/live",
    "type":"STREAM"
}
```

### HTTP Request

`PUT https://api.flowplayer.com/ovp/workspaces/:workspace_id/livesources/:livesource_id`


### Response parameters

Parameter | Description
--------- | -------------------------------------
id | Id for Livesource
name | Name for Livesource
description | Description for Livesource
type | Type of Livesource. Currently there are two types of Livesources, `STREAM` and `REMOTE`.
stream_name | Identifier for the Livesource on our livestreaming servers. This shall be used in your broadcast software to identify this Livesource. This is not relevant for `REMOTE` Livesources.
ingest_url | Url to our livestreaming servers. This shall be used in your broadcast software to send your input to the correct livestreaming server for this Livesource. This is not relevant for `REMOTE` Livesources.
remote_hls_url | Only exists on Livesources with `REMOTE`-type. This url is used by the enduser to view the stream in the player.

### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified Workspace or Livesource is not found

## Create Livesource

Endpoint for creating a Livesource

> Endpoint for creating a Livesource

```shell
curl "https://api.flowplayer.com/ovp/workspaces/:workspace_id/livesources"
```

```json
{
    "id": "951ba340-2949-4299-9b55-5d33b3bc9a5e",
    "name": "Flowplayer Livesource",
    "description": "On Office computer",
    "stream_name": "8fbpE5iA",
    "ingest_url": "rtmp://sample.input.flowplayer.com:1935/live",
    "type":"STREAM"
}
```

### HTTP Request

`PUT https://api.flowplayer.com/ovp/workspaces/:workspace_id/livesources`


### Request parameters

Parameter | Description
--------- | -------------------------------------
name      | The Livesource name.
description     | `optional` The Livesource description.
type | Type of Livesource. Currently there are two types of Livesources, `STREAM` and `REMOTE`. Use `STREAM` when you want a Livesource that you use for streaming to Flowplayer's Livestreaming environment and `REMOTE` when you have a HLS-stream that you want to stream directly to the player. When `REMOTE` is selected `remote_hls_url` must be specified.
remote_hls_url | Only exists on Livesources with `REMOTE`-type. This url is used by the enduser to view the stream in the player.


### Response parameters

Parameter | Description
--------- | -------------------------------------
id | Id for Livesource
name | Name for Livesource
description | Description for Livesource
type | Type of Livesource. Currently there are two types of Livesources, `STREAM` and `REMOTE`.
stream_name | Identifier for the Livesource on our livestreaming servers. This shall be used in your broadcast software to identify this Livesource. This is not relevant for `REMOTE` Livesources.
ingest_url | Url to our livestreaming servers. This shall be used in your broadcast software to send your input to the correct livestreaming server for this Livesource. This is not relevant for `REMOTE` Livesources.
remote_hls_url | Only exists on Livesources with `REMOTE`-type. This url is used by the enduser to view the stream in the player.


### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified Workspace is not found
422         | If some invalid input properties are used in the request

## Update Livesource

Endpoint for updating a Livesource. The only fields that can be updated for a Livesource is `name`, `description` and `remote_hls_url`. Other fields such as `stream_name`, `ingest_url` and `REMOTE` are final and can't be changed once a Livesource have been created.

> Endpoint for updating a Livesource

```shell
curl "https://api.flowplayer.com/ovp/workspaces/:workspace_id/livesources"
```

```json
{
    "id": "951ba340-2949-4299-9b55-5d33b3bc9a5e",
    "name": "Flowplayer Livesource",
    "description": "On Office computer",
    "remote_hls_url":"https://flowplayer.com/ultimate_remote_livestream.m3u8"
}
```

### HTTP Request

`PUT https://api.flowplayer.com/ovp/workspaces/:workspace_id/livesources`


### Request parameters

Parameter | Description
--------- | -------------------------------------
id        | Id for the Livesource to by updated
name      | `optional` The Livesource name.
description     | `optional` The Livesource description.
remote_hls_url | Only editable for Livesources with `REMOTE`-type. This url is used by the enduser to view the stream in the player.


### Response parameters

Parameter | Description
--------- | -------------------------------------
id | Id for Livesource
name | Name for Livesource
description | Description for Livesource
type | Type of Livesource. Currently there are two types of Livesources, `STREAM` and `REMOTE`.
stream_name | Identifier for the Livesource on our livestreaming servers. This shall be used in your broadcast software to identify this Livesource. This is not relevant for `REMOTE` Livesources.
ingest_url | Url to our livestreaming servers. This shall be used in your broadcast software to send your input to the correct livestreaming server for this Livesource. This is not relevant for `REMOTE` Livesources.
remote_hls_url | Only exists on Livesources with `REMOTE`-type. This url is used by the enduser to view the stream in the player.


### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified Workspace is not found
422         | If some invalid input properties, only `id`, `name` and `description` are valid, are used in the request


## Delete Livesource

Endpoint for deleting a Livesource. When deleting a Livesource all Livestream that are setup to use the Livesource will be reconfigured with their default stream name.

The request is done as a `DELETE` with a body containing

> Endpoint for deleting a Livesource

```shell
curl "https://api.flowplayer.com/ovp/workspaces/:workspace_id/livesources/:livesource_id"
```

```json
{}
```

### HTTP Request

`DELETE https://api.flowplayer.com/ovp/workspaces/:workspace_id/livesources/:livesource_id`


### Request parameters

Parameter | Description
--------- | -------------------------------------
id        | Id for the Livesource to by deleted

### Response parameters

Parameter | Description
--------- | -------------------------------------

### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified Workspace or Livesource is not found


## Livesource Availability

List all livesource on a Workspace and their availability for during the selected timespan.

> List all livesource on a Workspace and their availability for during the selected timespan.


```shell
curl "https://api.flowplayer.com/ovp/workspaces/:workspace_id/livesources/available?timespan=2018-01-16T11:45:44+0100,2018-02-16T11:45:44+0100"
```

```json
{
    "site_id": "5a1d4283-7675-40eb-91dd-ec526aa8f643",
    "start": "2018-01-16T00:00:00+0100",
    "stop": "2018-02-16T00:00:00+0100",
    "sources": [
        {
            "id": "5a1d4283-7675-40eb-91dd-ec526aa8f643",
            "name": "Live U",
            "description": "",
            "stream_name": "eODqqR0w",
            "bookings": [
                {
                    "slot_id": "06e8d713-02a0-4ea8-9591-b3544fb90dd8",
                    "start": "2018-01-20T09:00:00+0100",
                    "stop": "2018-01-20T21:00:00+0100"
                }
            ]
        },
        {
            "id": "68d9dec0-45ad-4724-a60a-7ef36cd28a04",
            "name": "Studio",
            "description": "",
            "stream_name": "CgT8xhZd",
            "bookings": []
        }
    ]
}
```

### HTTP Request

`GET https://api.flowplayer.com/ovp/workspaces/:workspace_id/livesources/available?timespan=:starttime,:stoptime`

### Request parameters

Parameter | Description
--------- | -------------------------------------
timespan        | Start- and stopdate commaseperated in `yyyy-MM-dd'T'HH:mm:ssZ`-format.


### Response

Parameter | Description
--------- | -------------------------------------
site_id        | Workspace for all Livesources
start      | Start date of timespan
stop      | Stop date of timespan
sources[].id | Id for Livesource
sources[].name | Name for Livesource
sources[].bookings | Contains a list of all Livestreams that will use the Livesource during the timespan. If empty no bookings exists and the Livesource is available for use.
sources[].bookings[].slot_id | Id for Livestream.
sources[].bookings[].start | Starttime for Livestream formatted in `yyyy-MM-dd'T'HH:mm:ssZ`.
sources[].bookings[].stop | Stoptime for Livestream formatted in `yyyy-MM-dd'T'HH:mm:ssZ`.

### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified Workspace or Livesource is not found
