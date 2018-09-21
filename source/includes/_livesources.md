# Livesources

## List Livesources

List Livesources on a Workspace

> List Livesources on a Workspace


```shell
curl "https://app.flowplayer.com/ovp/workspaces/:workspace_id/livesources"
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
            "ingest_url": "rtmp://sample.input.flowplayer.com:1935/live"
        },
        {
            "id": "764335ee-bd56-4f1f-b610-f703ddaf6545",
            "name": "iPhone",
            "description": "In iPhone app",
            "stream_name": "Rpdo32",
            "ingest_url": "rtmp://sample.input.flowplayer.com:1935/live"
        }
    ]
}
```

### HTTP Request

`GET https://app.flowplayer.com/ovp/workspaces/:workspace_id/livesources`

### Request parameters

Parameter | Description
--------- | -------------------------------------
page        | `optional` - Page for response, default value is `0`.
page_size        | `optional` - Page size for response, default value is `20`.
search | `optional` - Search term for filtering the response. Searches `name`.
sort_by | `optional` - Sorting column for the response, default value is `name`. Possible values: `name`.
sort_order | `optional` - Sorting order for the response, default value is `desc`. Possible values `asc` and `desc`


### Response

Parameter | Description
--------- | -------------------------------------
assets[].id | Id for Live Source
assets[].name | Name for Live Source
assets[].description | Description for Livesource
assets[].stream_name | Identifier for the Livesource on our livestreaming servers. This shall be used in your broadcast software to identify this Livesource. 
assets[].ingest_url | Url to our livestreaming servers. This shall be used in your broadcast software to send your input to the correct livestreaming server for this Livesource. 

### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified Workspace or Livecast is not found


## Get Livesource

Endpoint for fetching one Livesource

> Endpoint for fetching one Livesource

```shell
curl "https://app.flowplayer.com/ovp/workspaces/:workspace_id/livesource/:livesource_id"
```

```json
{
    "id": "951ba340-2949-4299-9b55-5d33b3bc9a5e",
    "name": "Flowplayer Livesource",
    "description": "On Office computer",
    "stream_name": "8fbpE5iA",
    "ingest_url": "rtmp://sample.input.flowplayer.com:1935/live"
}
```

### HTTP Request

`PUT https://app.flowplayer.com/ovp/workspaces/:workspace_id/livesource/:livesource_id`


### Response parameters

Parameter | Description
--------- | -------------------------------------
id | Id for Live Source
name | Name for Live Source
description | Description for Livesource
stream_name | Identifier for the Livesource on our livestreaming servers. This shall be used in your broadcast software to identify this Livesource. 
ingest_url | Url to our livestreaming servers. This shall be used in your broadcast software to send your input to the correct livestreaming server for this Livesource. 


## Create Livesource

Endpoint for creating a Livesource

> Endpoint for creating a Livesource

```shell
curl "https://app.flowplayer.com/ovp/workspaces/:workspace_id/livesource"
```

```json
{
    "id": "951ba340-2949-4299-9b55-5d33b3bc9a5e",
    "name": "Flowplayer Livesource",
    "description": "On Office computer",
    "stream_name": "8fbpE5iA",
    "ingest_url": "rtmp://sample.input.flowplayer.com:1935/live"
}
```

### HTTP Request

`PUT https://app.flowplayer.com/ovp/workspaces/:workspace_id/livesource`


### Request parameters

Parameter | Description
--------- | -------------------------------------
name      | The Livesource name.
description     | `optional` The Livesource description.

### Response parameters

Parameter | Description
--------- | -------------------------------------
id | Id for Live Source
name | Name for Live Source
description | Description for Livesource
stream_name | Identifier for the Livesource on our livestreaming servers. This shall be used in your broadcast software to identify this Livesource. 
ingest_url | Url to our livestreaming servers. This shall be used in your broadcast software to send your input to the correct livestreaming server for this Livesource. 


## Update Livesource

Endpoint for updating a Livesource. The only fields that can be updated for a Livesource is `name` and `description`. Other fields such as `stream_name` and `ingest_url` are final and can't be altered once a Livesource have been created.

> Endpoint for updating a Livesource

```shell
curl "https://app.flowplayer.com/ovp/workspaces/:workspace_id/livesource"
```

```json
{
    "id": "951ba340-2949-4299-9b55-5d33b3bc9a5e",
    "name": "Flowplayer Livesource",
    "description": "On Office computer",
    "stream_name": "8fbpE5iA",
    "ingest_url": "rtmp://sample.input.flowplayer.com:1935/live"
}
```

### HTTP Request

`PUT https://app.flowplayer.com/ovp/workspaces/:workspace_id/livesource`


### Request parameters

Parameter | Description
--------- | -------------------------------------
id        | Id for the Livesource to by updated
name      | `optional` The Livesource name.
description     | `optional` The Livesource description.

### Response parameters

Parameter | Description
--------- | -------------------------------------
id | Id for Live Source
name | Name for Live Source
description | Description for Livesource
stream_name | Identifier for the Livesource on our livestreaming servers. This shall be used in your broadcast software to identify this Livesource. 
ingest_url | Url to our livestreaming servers. This shall be used in your broadcast software to send your input to the correct livestreaming server for this Livesource. 

## Livesources Available

List all livesource on a Workspace and their availability for during the selected timespan.

> List all livesource on a Workspace and their availability for during the selected timespan.


```shell
curl "https://app.flowplayer.com/ovp/workspaces/:workspace_id/livesources/available?timespan=2018-01-16T11:45:44+0100,2018-02-16T11:45:44+0100"
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

`GET https://app.flowplayer.com/ovp/workspaces/:workspace_id/livesources/available?timespan=:starttime,:stoptime`

### Request parameters

Parameter | Description
--------- | -------------------------------------
timespan        | Start- and stopdate commaseperated in `yyyy-MM-dd'T'HH:mm:ssZ`-format.


### Response

Parameter | Description
--------- | -------------------------------------
site_id        | Workspace for all Live Sources
start      | Start date of timespan
stop      | Stop date of timespan
sources[].id | Id for Live Source
sources[].name | Name for Live Source
sources[].bookings | Contains a list of all Livecasts that will use the Live Source during the timespan. If empty no bookings exists and the Live Source is available for use.
sources[].bookings[].slot_id | Id for Livecast.
sources[].bookings[].start | Starttime for Livecast formatted in `yyyy-MM-dd'T'HH:mm:ssZ`.
sources[].bookings[].stop | Stoptime for Livecast formatted in `yyyy-MM-dd'T'HH:mm:ssZ`.

### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified Workspace or Livecast is not found


