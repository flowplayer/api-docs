# Livecasts

## Get Livecast

Endpoint for fetching infomation about one single livecast

> Endpoint for fetching infomation about one single livecast

```shell
curl "https://app.flowplayer.com/ovp/sites/{site_id}/livecasts/{livecast_id}"
```

```json
{
    "id": "06e8d713-02a0-4ea8-9591-b3544fb90dd8",
    "name": "Flowplayer Livcast",
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

`GET https://app.flowplayer.com/ovp/sites/:site_id/livecast/:livecast_id`


### Request parameters

### Response

Parameter | Description
--------- | -------------------------------------
id        | The livecast Id
name      | The livecasts name, can be displayed in the player.
description     | The livecasts description, can be displayed in the player.
is_connected       | Is `true` if somebody is broadcasting on either the `stream_name` or `live_source` configured with this livecast.
starttime | The starttime for the livecast formatted in `yyyy-MM-dd'T'HH:mm:ssZ`. Before the starttime the livecast will not be publically visible in the player.
stoptime | The stoptime for the livecast formatted in `yyyy-MM-dd'T'HH:mm:ssZ`. This do not have any effect for the playback in the player and the player will not stop an ongoing livecast although the stoptime has passed.
created_at | The creation date formatted in `yyyy-MM-dd'T'HH:mm:ssZ`.
updated_at | The latest update formatted in `yyyy-MM-dd'T'HH:mm:ssZ`.
category_id        | The livecasts category
user_id        | Id for the creator of the livecast
noads        | If true no ads will be displayed during this livecast.
published    | If true this livecast will be available for listings in the public API and also as related.
tags | A commaseperated list of tags. 
scheduling_type | The livecast's type. Possible values `instant`, `scheduled`, `linear`. This value can't be changed once the livecast has been created. In our UI the values are presented as `Go Live now`, `Scheduled` and `24x7`.
live_source | If not `null` the Live Source that is used for this livecast. 
live_source.id | Id of the Live Source
live_source.name | Name of the Live Source
live_source.stream_name | This can be ignored, use the one specified in `stream.stream_name` .
live_source.ingest_url | This can be ignored, use the one specified in `stream.ingest_url` .
stream | Settings for streaming this livecast
stream.stream_name | Identifier for the livecast on our livestreaming servers. This shall be used in your broadcast software to identify this livecast. 
stream.ingest_url | Url to our livestreaming servers. This shall be used in your broadcast software to send your input to the correct livestreaming server for this livecast. 
stream.viewing_url | Url that the player uses to stream this livecast.
stream.quality_type | Specifies what quality settings the livestreaming server will use while transcoding your input stream.
stream.dvr | Use DVR for this livecast.
record | Recording settings for this livecast
record.auto_record | If this livecast should be automatically recorded. It will start recording on this livecast selected starttime. All recordings will be available as VoD.
record.auto_replace_<br>with_recording | When the first recording of this livecast is done it will replace the livecast. 
video | Describes video and display settings related to this livecast. 
video.video_id | If `null` no video is connected otherwise it's the id for the video that possibly will be displayed instead of the livecast.
video.display_video | When this is set as `true` and a `video_id` is set the player will render that video instead of the livecast. It will rendered the video regardless if your broadcast live on this livecast or not.
video.display_video_<br>when_not_broadcasting | `Deprecated`


### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified Site or Livecast is not found


## List Livecasts

Endpoint for fetching infomation about livecasts on a specific Site. The response is list of livecasts and for each livecast it contains a subset of the information available in the `get livecast`-request.

> Endpoint for fetching infomation about livecasts on a specific Site.

```shell
curl "https://app.flowplayer.com/ovp/sites/{site_id}/livecasts/?search=flowplayer"
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

`GET https://app.flowplayer.com/ovp/sites/:site_id/livecasts/`


### Request parameters

Parameter | Description
--------- | -------------------------------------
categories        | `optional` - Commaseperated list of categories ids that livecasts must belong to.
page        | `optional` - Page for response, default value is `0`.
page_size        | `optional` - Page size for response, default value is `20`.
search | `optional` - Search term for filtering the response. Searches `name`, `description` and `tags`.
sort_by | `optional` - Sorting column for the response, default value is `created_at`. Possible values: `created_at`, `name` and `starttime`.
sort_order | `optional` - Sorting order for the response, default value is `desc`. Possible values `asc` and `desc`
filter | `optional` - Can be used to filter out livecasts from their starttimes. Possible values are `upcoming` or `recent`. `upcoming` will present all livecasts that have a starttime from 24h before now and forward and will be order with the one with earliest starttime first. `recent` will present all livecasts that have a starttime from 24h from now and before and will be order with the one with most recent starttime first.

### Response

Parameter | Description
--------- | -------------------------------------
id        | The livecast Id
name      | The livecasts name, can be displayed in the player.
description     | The livecasts description, can be displayed in the player.
is_connected       | Is `true` if somebody is broadcasting on either the `stream_name` or `live_source` configured with this livecast.
starttime | The starttime for the livecast formatted in `yyyy-MM-dd'T'HH:mm:ssZ`. Before the starttime the livecast will not be publically visible in the player.
stoptime | The stoptime for the livecast formatted in `yyyy-MM-dd'T'HH:mm:ssZ`. This do not have any effect for the playback in the player and the player will not stop an ongoing livecast although the stoptime has passed.
created_at | The creation date formatted in `yyyy-MM-dd'T'HH:mm:ssZ`.
updated_at | The latest update formatted in `yyyy-MM-dd'T'HH:mm:ssZ`.
category_id        | The livecasts category
scheduling_type | The livecasts type. Possible values `instant`, `scheduled`, `linear`. These values can't be changed once the livecast has been created. In our UI the values are presented as `Go Live now`, `Scheduled` and `24x7`.

### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified Site or Livecast is not found


## Create Livecast

Endpoint for creating a livecast

> Endpoint for creating a livecast

```shell
curl "https://app.flowplayer.com/ovp/sites/{site_id}/livecast"
```

```json
{
    "name": "Flowplayer Livcast",
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

`PUT https://app.flowplayer.com/ovp/sites/:site_id/livecast`


### Request parameters

Parameter | Description
--------- | -------------------------------------
name      | The livecasts name, can be displayed in the player.
description     | `optional` The livecasts description, can be displayed in the player.
starttime | The starttime for the livecast formatted in `yyyy-MM-dd'T'HH:mm:ssZ`. Before the starttime the livecast will not be publically visible in the player.
stoptime | The stoptime for the livecast formatted in `yyyy-MM-dd'T'HH:mm:ssZ`. This do not have any effect for the playback in the player and the player will not stop an ongoing livecast although the stoptime has passed.
category_id        | `optional` The livecasts category. If not provided the Sites default category will be used.
user_id        | `optional` Id for the creator of the livecast
noads        | `optional` If true no ads will be displayed during this livecast.
published    | `optional` If true this livecast will be available for listings in the public API and also as related. Default value is `false`.
tags | `optional` A commaseperated list of tags. 
scheduling_type | `optional` The livecasts type. Possible values `instant`, `scheduled`, `linear`. These values can't be changed once the livecast has been created. Default value is `instant`.
live_source | `optional` If not `null` the Live Source that is used for this livecast.
live_source.id | Id of the Live Source
stream | Settings for streaming this livecast
stream.viewing_url | `optional` Url that the player uses to stream this livecast. This can only be set if no Live Source is selected. Changing this should only be done if you have an external source that doesn't use our Livestreaming servers.
stream.quality_type | `optional` Specifies what quality settings the livestreaming server will use while transcoding your input stream. Default is set to `Normal`.
stream.dvr | `optional` Use DVR for this livecast. Only available if DVR is activated on your account. Default is set to `false`.
record | Recording settings for this livecast
record.auto_record | If this livecast should be automatically recorded. It will start recording on this livecast selected starttime. All recordings will be available as VoD. Default settings depends upon you Site settings.
record.auto_replace_<br>with_recording | When the first recording of this livecast is done it will replace the livecast. Default settings depends upon you Site settings.
video | Describes video and display settings related to this livecast. 
video.video_id | If `null` no video is connected otherwise it's the id for the video that possibly will be displayed instead of the livecast. Default is set to `null`.
video.display_video | When this is set as `true` and a `video_id` is set the player will render that video instead of the livecast. It will rendered the video regardless if your broadcast live on this livecast or not. Default is set to `false`.
video.display_video_<br>when_not_broadcasting | `Deprecated`

## Update Livecast

Endpoint for updating a livecast

> Endpoint for updating a livecast

```shell
curl "https://app.flowplayer.com/ovp/sites/:siteId/livecast/:livecastId"
```

```json
{
	"id":"fa81a81d-bdef-4672-9695-b73d71044937"
    "name": "Flowplayer Livcast",
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

`PUT https://app.flowplayer.com/ovp/sites/:site_id/livecast/:livecast_id`


### Request parameters

Parameter | Description
--------- | -------------------------------------
id      | 
name      | `optional` The livecasts name, can be displayed in the player.
description     | `optional` The livecasts description, can be displayed in the player.
starttime | `optional` The starttime for the livecast formatted in `yyyy-MM-dd'T'HH:mm:ssZ`. Before the starttime the livecast will not be publically visible in the player.
stoptime |  `optional` The stoptime for the livecast formatted in `yyyy-MM-dd'T'HH:mm:ssZ`. This do not have any effect for the playback in the player and the player will not stop an ongoing livecast although the stoptime has passed.
category_id        | `optional` The livecasts category. If not provided the Sites default category will be used.
user_id        | `optional` Id for the creator of the livecast
noads        | `optional` If true no ads will be displayed during this livecast.
published    | `optional` If true this livecast will be available for listings in the public API and also as related. Default value is `false`.
tags | `optional` A commaseperated list of tags. 
live_source | If not `null` the Live Source that is used for this livecast. To remove a live source from a Livecast you need to set the Id for the live source to "". Just setting the `live_source` to `null` will not remove the live source. 
live_source.id | Id of the Live Source
stream | Settings for streaming this livecast
stream.viewing_url | `optional` Url that the player uses to stream this livecast. This can only be set if no Live Source is selected. Changing this should only be done if you have an external source that doesn't use our Livestreaming servers.
stream.quality_type | `optional` Specifies what quality settings the livestreaming server will use while transcoding your input stream. Default is set to `Normal`.
stream.dvr | `optional` Use DVR for this livecast. Only available if DVR is activated on your account. Default is set to `false`.
record | Recording settings for this livecast
record.auto_record | If this livecast should be automatically recorded. It will start recording on this livecast selected starttime. All recordings will be available as VoD. Default settings depends upon you Site settings.
record.auto_replace_<br>with_recording | When the first recording of this livecast is done it will replace the livecast. Default settings depends upon you Site settings.
video | Describes video and display settings related to this livecast. To remove a video from a Livecast you need to set the Id for the video to "". Just setting the `video` to `null` will not remove the video.  
video.video_id | If `null` no video is connected otherwise it's the id for the video that possibly will be displayed instead of the livecast. Default is set to `null`.
video.display_video | When this is set as `true` and a `video_id` is set the player will render that video instead of the livecast. It will rendered the video regardless if your broadcast live on this livecast or not. Default is set to `false`.
video.display_video_<br>when_not_broadcasting | `Deprecated`


## Delete Livecast

Endpoint for deleting one single livecast

> Endpoint for deleting one single livecast


```shell
curl -X DELETE "https://app.flowplayer.com/ovp/sites/{site_id}/livecasts/{livecast_id}"
```

```json
{
	"success":"ok"
}
```

### HTTP Request

`DELETE https://app.flowplayer.com/ovp/sites/:site_id/livecast/:livecast_id`

### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified Site or Livecast is not found

## Send Configuration Email

Endpoint for sending email with broadcasting configuration details for one livecast.

> Endpoint for deleting one single livecast


```shell
curl "https://app.flowplayer.com/ovp/sites/{site_id}/livecasts/{livecast_id}/send-configuration-email?email=hello@flowplayer.com"
```

```json
{
	"success":"ok"
}
```

### HTTP Request

`GET https://app.flowplayer.com/ovp/sites/:site_id/livecast/:livecast_id/send-configuration-email`

### Request parameters

Parameter | Description
--------- | -------------------------------------
email        |  One email address that the backend will send the configuration email to.


### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified Site or Livecast is not found

