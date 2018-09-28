# LiveClips

## Get LiveClips

Endpoint for fetching infomation about all liveclips associated to a single livestream

> Endpoint for fetching infomation about all liveclips associated to a single livestream

```shell
curl "https://app.flowplayer.com/ovp/workspaces/{siteId}/livestreams/{livestreamId}/clips"
```

```json
{
    "query": null,
    "total_count": 1,
    "total_count_in_search": 1,
    "page": 0,
    "page_size": 20,
    "total_pages": 1,
    "search_term": "",
    "assets": [
        {
            "id": "dcf264b9-40c3-4239-b2d7-52704b5ffb24",
            "site_id": "7F000001:011D4302AE97:4FA8:0161DF2A",
            "stream_name": "5matU1TV",
            "livestream_id": "3bd77b07-1ab5-45cb-af26-da9e14f15e4c",
            "s3_bucket": "stdlwcdn",
            "s3_path": "livecliping/5matU1TV/_2018-09-25-11.46.50",
            "play_list_name": "playlist.m3u8",
            "start_time": "2018-09-25T11:46:50+0200",
            "stop_time": null,
            "play_list_url": "http://l3video.lwcdn.com/livecliping/5matU1TV/_2018-09-25-11.46.50/playlist.m3u8",
            "duration": 858,
            "break_points": [
                0,
                4.6,
                10.167,
                16.167,
                22.167,
                29.966,
                35.967,
                41.999,
                .
                .
                .
                .
                .
                .
                .
                .
                .
                .
                838.333,
                846.033,
                852.033,
                858.033
            ]
        }
    ]
}
```

### HTTP Request

`GET https://app.flowplayer.com/ovp/workspaces/{siteId}/livestreams/{livestreamId}/clips`


### Request parameters
Parameter | Description
--------- | -------------------------------------
page        | `optional` - Page for response, default value is `0`.
page_size        | `optional` - Page size for response, default value is `20`.
sort_by | `optional` - Sorting column for the response, default value is `startTime`. Possible values: `startTime,stopTime`.
sort_order | `optional` - Sorting order for the response, default value is `desc`. Possible values `asc` and `desc`


### Response
Parameter | Description
--------- | -------------------------------------
assets[].id | Id for Live Clip Recording
assets[].site_id | The id the of the site the live cliup belongs to
assets[].stream_name | The name of the stream the live clip is from.
assets[].livestream_id | The id of the live stream the clip belongs to.
assets[].s3_bucket | The S3 bucket of the clip. 
assets[].s3_path | The path to the clip on S3.
assets[].play_list_name | The name of the playlist file.
assets[].start_time | The start time of the live clipping window. 
assets[].stop_time | The end time of the live clipping window, if the stream is still ongoing this will be empty.
assets[].play_list_url | This is the playlist that can be used in a player to play the current clip as a vod. If the stream is ongoing this can be called over and over to get the latest playlist. It will grow and grow as more of the stream is being produced.
assets[].duration | The duration of the possible clip when the call was made. If the clip is ongoing this will of course be changing constantly.
assets[].break_points | The points in time between segments in the clip. That is where a clip can be made.  

### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified Workspace is not found







## Create Vod from a live clip

Endpoint for creating a video from a live clip.

> Endpoint for creating a video from a live clip.


```json
body:
  {
    "name":"The name of the video to be created",
    "description":"The description of the video to be created",
    "tags":"tag1,tag2",
    "start_time":"78.1",
    "stop_time":"756.266"
    
    }

```
```json
{
    "id": "94321874-2aa3-4d58-a256-b6fd588218ff",
    "name": "The name of the video to be created",
    "description": "The description of the video to be created",
    "duration": 66,
    "unpublish": false,
    "unpublish_date": "2018-09-27T16:21:13+0200",
    "publish_date": "2018-09-27T16:21:13+0200",
    "created": "2018-09-27T16:21:13+0200",
    "updated": "2018-09-27T16:21:13+0200",
    "tags": "tag1,tag2",
    "state": "FINISHED",
    "encoding_progress": 100,
    "upload_progress": 100,
    "error_message": "",
    "remote": false,
    "deactivated": false,
    "images": [
        {
            "type": "thumbnail",
            "url": "http://l3video.lwcdn.com/i/v-i-94321874-2aa3-4d58-a256-b6fd588218ff-0.jpg"
        },
        {
            "type": "image",
            "url": "http://l3video.lwcdn.com/i/v-i-94321874-2aa3-4d58-a256-b6fd588218ff-1.jpg"
        }
    ],
    "no_ads": false
}
```



### HTTP Request

`PUT https://app.flowplayer.com/ovp/workspaces/{siteId}/livestreams/clip/{clipId}/video`

### Request parameters

Parameter | Description
--------- | -------------------------------------
name | The name of the new video.
description | The description of the new video.
tags | A comma separated list of tags for the new video.
start_time | Where in the clip to put the starting point of the new video. Can be any floating point number that is inside the duration, but if it is not one of the numbers returned in the get call. It will be rounded to the next value in that list.
stop_time | Where in the clip to put the out point of the video. Can be any floating point number, but if it is not one of the numbers from the get request it will be rounded to the previous one in that list.


### Response
The video created from the live clip.
### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified lives clip is not found

