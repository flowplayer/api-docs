# Livestreams

## Get Livestream

Endpoint for fetching infomation about one single livestream

> Endpoint for fetching infomation about one single livestream

```shell
curl "https://app.flowplayer.com/ovp/workspaces/:workspace_id/livestreams/{livestream_id}"
```

```json
{
    "id": "06e8d713-02a0-4ea8-9591-b3544fb90dd8",
    "name": "Flowplayer Livestream",
    "description": "",
    "is_connected": false,
    "starttime": "2018-11-16T09:00:00+0100",
    "stoptime": "2018-11-06T21:00:00+0100",
    "created_at": "2017-10-31T09:55:57+0100",
    "updated_at": "2018-02-14T15:52:48+0100",
    "category_id": "7F000001:011DED6174DF:9E73:013B8933",
    "scheduling_type":"instant",
    "images": [
        {
            "type": "thumbnail",
            "url": "https://stdlwcdn.lwcdn.com/mediaconvert/i/i-fa81a81d-bdef-4672-9695-b73d71044937124x70.jpg"
        },
        {
            "type": "image",
            "url": "https://stdlwcdn.lwcdn.com/mediaconvert/i/i-fa81a81d-bdef-4672-9695-b73d71044937.jpg"
        }
    ],
    "adkeyword": "",
    "noads": false,
    "published": true,
    "tags": "",
    "live_source": null,
    "stream": {
        "stream_name": "6a788d75-ef57-4cd2-b863-5a1bf6fc25a0",
        "viewing_url": "http://live.flowplayer.com/playlist.m3u8",
        "ingest_url": "rtmp://input.flowplayer.com:1935/live",
        "quality_type": "NORMAL",
        "dvr": true
    },
    "record": {
        "auto_record": true,
        "auto_replace_with_recording": false
    },
    "user_id": "141dfa73-971b-4816-8572-928599d2b81b",
    "video": {
        "video_id": null,
        "display_video": true,
        "display_video_when_not_broadcasting": false
    }
}
```

### HTTP Request

`GET https://app.flowplayer.com/ovp/workspaces/:workspace_id/livestreams/:livestream_id`


### Request parameters

### Response

Parameter | Description
--------- | -------------------------------------
id        | The livestream Id
name      | The livestreams name, can be displayed in the player.
description     | The livestreams description, can be displayed in the player.
is_connected       | Is `true` if somebody is broadcasting on either the `stream_name` or `live_source` configured with this livestream.
starttime | The starttime for the livestream formatted in `yyyy-MM-dd'T'HH:mm:ssZ`. Before the starttime the livestream will not be publically visible in the player.
stoptime | The stoptime for the livestream formatted in `yyyy-MM-dd'T'HH:mm:ssZ`. This do not have any effect for the playback in the player and the player will not stop an ongoing livestream although the stoptime has passed.
created_at | The creation date formatted in `yyyy-MM-dd'T'HH:mm:ssZ`.
updated_at | The latest update formatted in `yyyy-MM-dd'T'HH:mm:ssZ`.
category_id        | The livestreams category
user_id        | Id for the creator of the livestream
noads        | If true no ads will be displayed during this livestream.
published    | If true this livestream will be available for listings in the public API and also as related.
tags | A commaseperated list of tags. 
scheduling_type | The livestream's type. Possible values `instant`, `scheduled`, `linear`. This value can't be changed once the livestream has been created. In our UI the values are presented as `Go Live now`, `Scheduled` and `24x7`.
live_source | If not `null` the Live Source that is used for this livestream. 
live_source.id | Id of the Live Source
live_source.name | Name of the Live Source
live_source.stream_name | This can be ignored, use the one specified in `stream.stream_name` .
live_source.ingest_url | This can be ignored, use the one specified in `stream.ingest_url` .
stream | Settings for streaming this livestream
stream.stream_name | Identifier for the livestream on our livestreaming servers. This shall be used in your broadcast software to identify this livestream. 
stream.ingest_url | Url to our livestreaming servers. This shall be used in your broadcast software to send your input to the correct livestreaming server for this livestream. 
stream.viewing_url | Url that the player uses to stream this livestream.
stream.quality_type | Specifies what quality settings the livestreaming server will use while transcoding your input stream.
stream.dvr | Use DVR for this livestream.
record | Recording settings for this livestream
record.auto_record | If this livestream should be automatically recorded. It will start recording on this livestream selected starttime. All recordings will be available as VoD.
record.auto_replace_<br>with_recording | When the first recording of this livestream is done it will replace the livestream. 
video | Describes video and display settings related to this livestream. 
video.video_id | If `null` no video is connected otherwise it's the id for the video that possibly will be displayed instead of the livestream.
video.display_video | When this is set as `true` and a `video_id` is set the player will render that video instead of the livestream. It will rendered the video regardless if your broadcast live on this livestream or not.
video.display_video_<br>when_not_broadcasting | `Deprecated`


### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified Workspace or livestream is not found


## List livestreams

Endpoint for fetching infomation about livestreams on a specific Workspace. The response is list of livestreams and for each livestream it contains a subset of the information available in the `get livestream`-request.

> Endpoint for fetching infomation about livestreams on a specific Workspace.

```shell
curl "https://app.flowplayer.com/ovp/workspaces/:workspace_id/livestreams?query={"filters:[ {"key":"category" , "value" : ["category_id_1", "category_id_2"]},{"key":"remote", "value" : true}, {"key":"scheduling_type", "value" : ["instant","linear"]},{"key":"time_range","value":"active"}],"search" :"flowplayer","sort" : { "by":"name","order":"asc"},"page":0, "page_size":20}"
```

```json
{
    "total_count": 21,
    "total_count_in_search": 1,
    "page": 0,
    "page_size": 20,
    "total_pages": 1,
    "search_term": "flowplayer",
    "assets": [
        {
            "id": "f076a34e-6f54-4206-8d53-72a11c604b17",
            "name": "LIVE: Flowplayer office camera",
            "description": "Derby i Balderhallen 20 september.",
			"is_connected": true,
            "scheduling_type":"linear",
            "starttime": "2017-09-22T10:00:22+0200",
            "stoptime": "2017-09-22T10:00:22+0200",
            "created_at": "2017-09-19T20:06:03+0200",
            "updated_at": "2017-09-21T12:17:22+0200",
            "category_id": "1b61e759-bbf4-4a78-83b4-19d0ff0962fa",
            "images": [
                {
                    "type": "thumbnail",
                    "url": "http://cdn.flowplayer.com/i-bvYU0RZd1-124x70.jpg"
                },
                {
                    "type": "image",
                    "url": "http://pa9ab85da.lwcdn.com/i-bvYU0RZd1.jpg"
                }
            ]
        }
    ]
}
```



### HTTP Request

`GET https://app.flowplayer.com/ovp/workspaces/:workspace_id/livestreams/`


### Request parameters

Parameter | Description
--------- | -------------------------------------
filters | It's possible to use multiple different filters in the query. The different filter keys are listed below.
key.category | `optional` - The values should be an array of category ids that livestreams must belong to.
key.live_source | `optional` - The values should be an array of live source ids that livestreams must belong to.
key.remote | `optional` - To list only remote or non remote livestreams. Accepted values are `true` or `false`.
key.broadcast_status | `optional` - The values should be an array of strings. Accepted statuses are `not_yet_started`, `started`, `scheduled`, `unknown`.
key.scheduling_type | `optional` - The values should be an array of strings. Accepted statuses are `instant`, `scheduled`, `linear`.
page        | `optional` - Page for response, default value is `0`.
page_size        | `optional` - Page size for response, default value is `20`.
search | `optional` - Search term for filtering the response. Searches `name`, `description` and `tags`.
sort_by | `optional` - Sorting column for the response, default value is `created_at`. Possible values: `created_at`, `name` and `starttime`.
sort_order | `optional` - Sorting order for the response, default value is `desc`. Possible values `asc` and `desc`
filter | `optional` - Can be used to filter out livestreams from their starttimes. Possible values are `upcoming` or `recent`. `upcoming` will present all livestreams that have a starttime from 24h before now and forward and will be order with the one with earliest starttime first. `recent` will present all livestreams that have a starttime from 24h from now and before and will be order with the one with most recent starttime first.

### Response

Parameter | Description
--------- | -------------------------------------
id        | The livestream Id
name      | The livestreams name, can be displayed in the player.
description     | The livestreams description, can be displayed in the player.
is_connected       | Is `true` if somebody is broadcasting on either the `stream_name` or `live_source` configured with this livestream.
starttime | The starttime for the livestream formatted in `yyyy-MM-dd'T'HH:mm:ssZ`. Before the starttime the livestream will not be publically visible in the player.
stoptime | The stoptime for the livestream formatted in `yyyy-MM-dd'T'HH:mm:ssZ`. This do not have any effect for the playback in the player and the player will not stop an ongoing livestream although the stoptime has passed.
created_at | The creation date formatted in `yyyy-MM-dd'T'HH:mm:ssZ`.
updated_at | The latest update formatted in `yyyy-MM-dd'T'HH:mm:ssZ`.
category_id        | The livestreams category
scheduling_type | The livestreams type. Possible values `instant`, `scheduled`, `linear`. These values can't be changed once the livestream has been created. In our UI the values are presented as `Go Live now`, `Scheduled` and `24x7`.

### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified Workspace or livestream is not found


## Create livestream

Endpoint for creating a livestream

> Endpoint for creating a livestream

```shell
curl "https://app.flowplayer.com/ovp/workspaces/:workspace_id/livestreams"
```

```json
{
    "name": "Flowplayer Livestream",
    "description": "",
    "is_connected": false,
    "starttime": "2018-11-16T09:00:00+0100",
    "stoptime": "2018-11-06T21:00:00+0100",
    "created_at": "2017-10-31T09:55:57+0100",
    "updated_at": "2018-02-14T15:52:48+0100",
    "category_id": "7F000001:011DED6174DF:9E73:013B8933",
    "scheduling_type":"scheduled",
    "images": [
        {
            "type": "thumbnail",
            "url": "https://stdlwcdn.lwcdn.com/mediaconvert/i/i-fa81a81d-bdef-4672-9695-b73d71044937124x70.jpg"
        },
        {
            "type": "image",
            "url": "https://stdlwcdn.lwcdn.com/mediaconvert/i/i-fa81a81d-bdef-4672-9695-b73d71044937.jpg"
        }
    ],
    "adkeyword": "",
    "noads": false,
    "published": true,
    "tags": "",
    "live_source": null,  
    "stream": {
        "viewing_url": "http://live.flowplayer.com/playlist.m3u8",
        "quality_type": "NORMAL",
        "dvr": true
    },
    "record": {
        "auto_record": true,
        "auto_replace_with_recording": false
    },
    "user_id": "141dfa73-971b-4816-8572-928599d2b81b",
    "video": {
        "video_id": null,
        "display_video": true,
        "display_video_when_not_broadcasting": false
    }
}
```

### HTTP Request

`PUT https://app.flowplayer.com/ovp/workspaces/:workspace_id/livestreams`


### Request parameters

Parameter | Description
--------- | -------------------------------------
name      | The livestreams name, can be displayed in the player.
description     | `optional` The livestreams description, can be displayed in the player.
starttime | The starttime for the livestream formatted in `yyyy-MM-dd'T'HH:mm:ssZ`. Before the starttime the livestream will not be publically visible in the player.
stoptime | The stoptime for the livestream formatted in `yyyy-MM-dd'T'HH:mm:ssZ`. This do not have any effect for the playback in the player and the player will not stop an ongoing livestream although the stoptime has passed.
category_id        | `optional` The livestreams category. If not provided the Workspaces default category will be used.
user_id        | `optional` Id for the creator of the livestream
noads        | `optional` If true no ads will be displayed during this livestream.
published    | `optional` If true this livestream will be available for listings in the public API and also as related. Default value is `false`.
tags | `optional` A commaseperated list of tags. 
scheduling_type | `optional` The livestreams type. Possible values `instant`, `scheduled`, `linear`. These values can't be changed once the livestream has been created. Default value is `instant`.
live_source | `optional` If not `null` the Live Source that is used for this livestream.
live_source.id | Id of the Live Source
stream | Settings for streaming this livestream
stream.viewing_url | `optional` Url that the player uses to stream this livestream. This can only be set if no Live Source is selected. Changing this should only be done if you have an external source that doesn't use our Livestreaming servers.
stream.quality_type | `optional` Specifies what quality settings the livestreaming server will use while transcoding your input stream. Default is set to `Normal`.
stream.dvr | `optional` Use DVR for this livestream. Only available if DVR is activated on your account. Default is set to `false`.
record | Recording settings for this livestream
record.auto_record | If this livestream should be automatically recorded. It will start recording on this livestream selected starttime. All recordings will be available as VoD. Default settings depends upon you Workspace settings.
record.auto_replace_<br>with_recording | When the first recording of this livestream is done it will replace the livestream. Default settings depends upon you Workspace settings.
video | Describes video and display settings related to this livestream. 
video.video_id | If `null` no video is connected otherwise it's the id for the video that possibly will be displayed instead of the livestream. Default is set to `null`.
video.display_video | When this is set as `true` and a `video_id` is set the player will render that video instead of the livestream. It will rendered the video regardless if your broadcast live on this livestream or not. Default is set to `false`.
video.display_video_<br>when_not_broadcasting | `Deprecated`

## Update livestream

Endpoint for updating a livestream

> Endpoint for updating a livestream

```shell
curl "https://app.flowplayer.com/ovp/workspaces/:siteId/livestreams/:livestreamId"
```

```json
{
	"id":"fa81a81d-bdef-4672-9695-b73d71044937"
    "name": "Flowplayer Livestream",
    "description": "",
    "is_connected": false,
    "starttime": "2018-11-16T09:00:00+0100",
    "stoptime": "2018-11-06T21:00:00+0100",
    "created_at": "2017-10-31T09:55:57+0100",
    "updated_at": "2018-02-14T15:52:48+0100",
    "category_id": "7F000001:011DED6174DF:9E73:013B8933",
    "images": [
        {
            "type": "thumbnail",
            "url": "https://stdlwcdn.lwcdn.com/mediaconvert/i/i-fa81a81d-bdef-4672-9695-b73d71044937124x70.jpg"
        },
        {
            "type": "image",
            "url": "https://stdlwcdn.lwcdn.com/mediaconvert/i/i-fa81a81d-bdef-4672-9695-b73d71044937.jpg"
        }
    ],
    "adkeyword": "",
    "noads": false,
    "published": true,
    "tags": "",
    "live_source": {
    	"id":"xodp23"
    },
    "record": {
        "auto_record": true,
        "auto_replace_with_recording": false
    },
    "user_id": "141dfa73-971b-4816-8572-928599d2b81b",
    "video": {
        "video_id": null,
        "display_video": false,
        "display_video_when_not_broadcasting": false
    }
}
```

### HTTP Request

`PUT https://app.flowplayer.com/ovp/workspaces/:workspace_id/livestream/:livestream_id`


### Request parameters

Parameter | Description
--------- | -------------------------------------
id      | 
name      | `optional` The livestreams name, can be displayed in the player.
description     | `optional` The livestreams description, can be displayed in the player.
starttime | `optional` The starttime for the livestream formatted in `yyyy-MM-dd'T'HH:mm:ssZ`. Before the starttime the livestream will not be publically visible in the player.
stoptime |  `optional` The stoptime for the livestream formatted in `yyyy-MM-dd'T'HH:mm:ssZ`. This do not have any effect for the playback in the player and the player will not stop an ongoing livestream although the stoptime has passed.
category_id        | `optional` The livestreams category. If not provided the Workspaces default category will be used.
user_id        | `optional` Id for the creator of the livestream
noads        | `optional` If true no ads will be displayed during this livestream.
published    | `optional` If true this livestream will be available for listings in the public API and also as related. Default value is `false`.
tags | `optional` A commaseperated list of tags. 
live_source | If not `null` the Live Source that is used for this livestream. To remove a live source from a livestream you need to set the Id for the live source to "". Just setting the `live_source` to `null` will not remove the live source. 
live_source.id | Id of the Live Source
stream | Settings for streaming this livestream
stream.viewing_url | `optional` Url that the player uses to stream this livestream. This can only be set if no Live Source is selected. Changing this should only be done if you have an external source that doesn't use our Livestreaming servers.
stream.quality_type | `optional` Specifies what quality settings the livestreaming server will use while transcoding your input stream. Default is set to `Normal`.
stream.dvr | `optional` Use DVR for this livestream. Only available if DVR is activated on your account. Default is set to `false`.
record | Recording settings for this livestream
record.auto_record | If this livestream should be automatically recorded. It will start recording on this livestream selected starttime. All recordings will be available as VoD. Default settings depends upon you Workspace settings.
record.auto_replace_<br>with_recording | When the first recording of this livestream is done it will replace the livestream. Default settings depends upon you Workspace settings.
video | Describes video and display settings related to this livestream. To remove a video from a livestream you need to set the Id for the video to "". Just setting the `video` to `null` will not remove the video.  
video.video_id | If `null` no video is connected otherwise it's the id for the video that possibly will be displayed instead of the livestream. Default is set to `null`.
video.display_video | When this is set as `true` and a `video_id` is set the player will render that video instead of the livestream. It will rendered the video regardless if your broadcast live on this livestream or not. Default is set to `false`.
video.display_video_<br>when_not_broadcasting | `Deprecated`


## Delete livestream

Endpoint for deleting one single livestream

> Endpoint for deleting one single livestream


```shell
curl -X DELETE "https://app.flowplayer.com/ovp/workspaces/:workspace_id/livestreams/{livestream_id}"
```

```json
{
	"success":"ok"
}
```

### HTTP Request

`DELETE https://app.flowplayer.com/ovp/workspaces/:workspace_id/livestream/:livestream_id`

### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified Workspace or livestream is not found

## Send Configuration Email

Endpoint for sending email with broadcasting configuration details for one livestream.

> Endpoint for deleting one single livestream


```shell
curl "https://app.flowplayer.com/ovp/workspaces/:workspace_id/livestreams/{livestream_id}/send-configuration-email?email=hello@flowplayer.com"
```

```json
{
	"success":"ok"
}
```

### HTTP Request

`GET https://app.flowplayer.com/ovp/workspaces/:workspace_id/livestream/:livestream_id/send-configuration-email`

### Request parameters

Parameter | Description
--------- | -------------------------------------
email        |  One email address that the backend will send the configuration email to.


### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified Workspace or livestream is not found

