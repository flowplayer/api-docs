# Analytics

## Get Video summarized analytics

This endpoint is used to query summarized analytics for a specific video. 

The video timeline is divided into 100 `segments` and every `segment` represents 1% for the video duration. The return value of this endpoint includes view counts for each of these 100 segments.

> Get analytics for video with ID 360b8f49-3c98-4020-ac72-83f958405239

```shell
curl "https://api.flowplayer.com/analytics/videos/360b8f49-3c98-4020-ac72-83f958405239?start=2018-01-01&end=2018-12-04"
```


```json
{
    "display" : 100,
    "plays" : {
        "total" : 20,
        "unique": 10,
        "device" : {
            "desktop": 11,
            "mobile" : 4,
            "tablet" : 5,
        },
        "mobile_os": {
            "android": 4,
            "ios": 5,
            "window_phone": 0
        }
    },
    "segments" : [10,9,9,...],
    "duration": 242,
    "completion_rate": 0.42,
    "average_completion": 0.59,
    "average_seconds_viewed": 143,
    "total_seconds_viewed": 246,
    "countries": [
        { "name": "Sweden", "plays": 11},
        { "name": "Finland", "plays": 9}
    ],
    "domains": [
        { "name": "flowplayer.com", "plays": 11},
        { "name": "home.com", "plays": 9}
    ],
    "players": [
        { "name":"frontpage player", "id": "xyz", "plays": 11},
        { "name":"demo player", "id": "xyz", "plays": 9}
    ],
    "date_from": "2018-03-01T00:00:00.000Z",
    "date_to": "2018-03-08T00:00:00.000Z",
}
```

### HTTP Request

`GET https://api.flowplayer.com/analytics/videos/:id`

### Request parameters

Parameter | Description
--------- | -------------------------------------
start     | optional, starting date/time of the interval, format `YYYY-MM-DDTHH` or `YYYY-MM-DD`
end       | optional, ending date/time of the interval, format `YYYY-MM-DDTHH` or `YYYY-MM-DD`
duration | optional, needed if the `total_seconds_viewed` and `average_seconds_viewed` should be calculated

### Response parameters

Parameter | Description
--------- | -------------------------------------
displays        | number of displays for this video. A `display` is registered when the player is completely loaded and ready to play the video. 
plays.total    | total number of plays for this video. A `play` is registered when the video starts to play. If the video have prerolls this is registered after all prerolls are complete.
plays.unique        | number of unique plays.
plays.device.desktop | number of plays on desktop
plays.device.mobile | number of plays on mobile
plays.device.tablet | number of plays on tablet
plays.mobile_os.android | number of plays on android
plays.mobile_os.ios | number of plays on ios
plays.mobile_os.windows_phone | number of plays on windows_phone
segments | number of viewers for each of the 100 segments of the video.
completion_rate | Number of viewers that viewed until the end presented with a decimal value. E.g. 0.42 means that 42% of the viewers viewed until the end.
average_completion | How long the viewers viewed in average presented in decimal value. E.g. 0.5 means that the average user viewed 50% of the video.
average_seconds_viewed | same as average_completion, but presented in seconds.
total_seconds_viewed | total engagement time in seconds
duration | duration of the video in seconds
countries | List containing plays per country sorted with the country with highest number of plays first.
domains | List containing plays per domain sorted with the domain with highest number of plays first.
players | List containing plays per player sorted with the player with highest number of plays first.

## Get Video timeseries analytics

This endpoint returns plays and display counts for specified time intervals.

> Get data for today, with a comparison to yesterday.

```shell
curl "https://api.flowplayer.com/analytics/videos/<video_id>/timeseries" 
```

> Returns  On 2018-04-21 it returned following:

```json
{
    "series": {
        "date_from": "2018-04-21T12:00:00.000Z",
        "date_to": "2018-04-22T12:00:00.000Z",
        "intervals": [{
            "time": "2018-04-22T12:00:00.000Z",
            "plays": 0,
            "displays": 0
        }],
        "total": {
            "displays": 0,
            "plays": 0
        }
    }
}
```

> Get hourly stats for three hours

```shell
curl "https://api.flowplayer.com/analytics/videos/{video_id}/timeline?start=2018-04-19T01&end=2018-04-19T04"
```

> Returns one intervals, one for the queried time range between 2018-05-01T00 and end=2018-05-01T03

```json
{
    "series": [{
        "date_from": "2018-04-18T19:00:00.000Z",
        "date_to": "2018-04-18T23:00:00.000Z",
        "intervals": [{
            "time": "2018-04-18T20:00:00.000Z",
            "plays": 29,
            "displays": 3174
        }, {
            "time": "2018-04-18T21:00:00.000Z",
            "plays": 25,
            "displays": 2581
        }, {
            "time": "2018-04-18T22:00:00.000Z",
            "plays": 21,
            "displays": 1558
        }, {
            "time": "2018-04-18T23:00:00.000Z",
            "plays": 14,
            "displays": 1245
        }],
        "total": {
            "displays": 8558,
            "plays": 89
        }
    }]
}
```

### HTTP Request

`GET https://api.flowplayer.com/analytics/videos/<video_id>/timeseries`

### Request parameters

Parameter | Description
--------- | -------------------------------------
start     | optional - start date and time, format `YYYY-MM-DDTHH` or `YYYY-MM-DD`. If not specified it will return analytics for the last seven days in daily interval.
end       | optional - end date and time, format `YYYY-MM-DDTHH` or `YYYY-MM-DD`
interval | optional - Specifies the interval timespan and possible values are `day` or `hour`. `Default` is `day`.

### Response parameters

Parameter | Description
--------- | -------------------------------------


## List Videos on Workspace

This endpoint returns videos having the most plays or displays on a Workspace during a specified period of time.

> Get the most played videos on a Workspace

```shell
curl "https://api.flowplayer.com/analytics/workspaces/<workspace_id>/videos" 
```

> 

```json
 [
        {
            "name": "video 1",
            "id": "360b8f49-3c98-4020-ac72-83f958405239",
            "plays": 252863,
            "displays":1234020
        },
        {
            "name": "video 2",
            "id": "3de6843f-2a65-46bd-a899-753d813f22c7",
            "plays": 227743,
            "displays":2131212
        },
        {
            "name": "video 3",
            "id": "9242781d-149e-468c-bc80-b383bc6fd73d",
            "plays": 210430,
            "displays":523223
        },
        {
            "name": "video 4",
            "id": "8ed589c1-9b88-4040-81f7-c063fcf139a2",
            "plays": 198156,
            "displays":234888
        },
        {
            "name": "video 5",
            "id": "666f6532-8b6e-4ccf-84a0-0916ab827a24",
            "plays": 192380,
            "displays":766543
        },
        {
            "name": "video 6",
            "id": "075d123a-8e58-4b05-b505-5f5ca8244a5d",
            "plays": 191079,
            "displays":237587
        },
        {
            "name": "video 7",
            "id": "0548e44c-253a-4bb0-bf89-4f3d83b95dde",
            "plays": 189647,
            "displays":867655
        },
        {
            "name": "video 8",
            "id": "6ebeec02-1f6c-45ef-a50e-eeaae4370da5",
            "plays": 184121,
            "displays":190001
        },
        {
            "name": "video 9",
            "id": "89a371e5-da85-4160-a913-b82b9a0e6b4c",
            "plays": 181421,
            "displays":238800
        },
        {
            "name": "video 10",
            "id": "bba4d3d9-ea9c-452f-83c3-e577c26a1784",
            "plays": 180103,
            "displays":188283
        }
]
```

> Get the most displays videos in a specific Workspace and in a specified time range, limiting the results to the top 3 videos.

```shell
curl "https://api.flowplayer.com/analytics/workspaces/54af42d8-b41d-4efc-b355-38d879820184/videos?size=3&start=2018-05-01&end=2018-05-31&sort=display"   
```

> Returns the three videos with most displays in Workspace `54af42d8-b41d-4efc-b355-38d879820184` during May 2018

```json
 [ 
    {
        "name": "video 1",
        "id": "360b8f49-3c98-4020-ac72-83f958405239",
        "plays": 252863,       
        "displays":2131212
    },
    {
        "name": "video 2",
        "id": "3de6843f-2a65-46bd-a899-753d813f22c7",
        "plays": 227743,
        "displays":1234020
    },
    {
        "name": "video 3",
        "id": "9242781d-149e-468c-bc80-b383bc6fd73d",
        "plays": 210430,
        "displays":523223
    }
 ]
```

### HTTP Request

`GET https://api.flowplayer.com/analytics/workspaces/<workspace_id>/videos`

### Request parameters

Parameter | Description
--------- | -------------------------------------
id    | The Workspace's Id is mandatory in the path.
start     | optional, start date and time, format `YYY-MM-DDTHH` or `YYY-MM-DD`
end       | optional, end date and time, format `YYY-MM-DDTHH` or `YYY-MM-DD`
size      | optional, maximum number of videos to be returned, 10 is returned if size is not specified. The request is limited to return 100 videos.
sort      | optional, sorting used when listing the videos. Possible values `displays` and `plays`. The default value is `plays`.


## Get Workspace summarized analytics

This endpoint is used to query summarized analytics for a specific workspace. 

The Workspace completion series is divided into 100 `segments` and every `segment` represents 1% for average videos duration. The return value of this endpoint includes view counts for each of these 100 segments.

> Get analytics for Workspace with Id 360b8f49-3c98-4020-ac72-83f958405239

```shell
curl "https://api.flowplayer.com/analytics/workspaces/360b8f49-3c98-4020-ac72-83f958405239?start=2018-01-01&end=2018-12-04"
```


```json
{
    "display" : 100,
    "plays" : {
        "total" : 20,
        "unique": 10,
        "device" : {
            "desktop": 11,
            "mobile" : 4,
            "tablet" : 5,
        },
        "mobile_os": {
            "android": 4,
            "ios": 5,
            "window_phone": 0
        }
    },
    "segments" : [10,9,9,...],
    "duration": 242,
    "completion_rate": 0.42,
    "average_completion": 0.59,
    "average_seconds_viewed": 143,
    "total_seconds_viewed": 246,
    "countries": [
        { "name": "Sweden", "plays": 11},
        { "name": "Finland", "plays": 9}
    ],
    "domains": [
        { "name": "flowplayer.com", "plays": 11},
        { "name": "home.com", "plays": 9}
    ],
    "players": [
        { "name":"frontpage player", "id": "xyz", "plays": 11},
        { "name":"demo player", "id": "xyz", "plays": 9}
    ],
    "date_from": "2018-03-01T00:00:00.000Z",
    "date_to": "2018-03-08T00:00:00.000Z",
}
```

### HTTP Request

`GET https://api.flowplayer.com/analytics/workspaces/<workspace_id>`

### Request parameters

Parameter | Description
--------- | -------------------------------------
start     | optional, starting date/time of the interval, format `YYYY-MM-DDTHH` or `YYYY-MM-DD`
end       | optional, ending date/time of the interval, format `YYYY-MM-DDTHH` or `YYYY-MM-DD`

### Response parameters

Parameter | Description
--------- | -------------------------------------
displays        | number of displays for this workspace. A `display` is registered when the player is completely loaded and ready to play the workspace. 
plays.total    | total number of plays for this workspace. A `play` is registered when the Workspace starts to play. If the Workspace have prerolls this is registered after all prerolls are complete.
plays.unique        | number of unique plays.
plays.device.desktop | number of plays on desktop
plays.device.mobile | number of plays on mobile
plays.device.tablet | number of plays on tablet
plays.mobile_os.android | number of plays on android
plays.mobile_os.ios | number of plays on ios
plays.mobile_os.windows_phone | number of plays on windows_phone
segments | number of viewers for each of the 100 segments of the videos for this workspace.
completion_rate | Number of viewers that viewed until the end presented with a decimal value. E.g. 0.42 means that 42% of the viewers viewed until the end.
average_completion | How long the viewers viewed in average presented in decimal value. E.g. 0.5 means that the average user viewed 50% of the workspace.
countries | List containing plays per country sorted with the country with highest number of plays first.
domains | List containing plays per domain sorted with the domain with highest number of plays first.
players | List containing plays per player sorted with the player with highest number of plays first.


## Get Category summarized analytics

This endpoint is used to query summarized analytics for a specific Category. 

The Category completion series is divided into 100 `segments` and every `segment` represents 1% for average videos duration. The return value of this endpoint includes view counts for each of these 100 segments.

> Get analytics for Category with Id 360b8f49-3c98-4020-ac72-83f958405239

```shell
curl "https://api.flowplayer.com/analytics/category/360b8f49-3c98-4020-ac72-83f958405239?start=2018-01-01&end=2018-12-04"
```


```json
{
    "display" : 100,
    "plays" : {
        "total" : 20,
        "unique": 10,
        "device" : {
            "desktop": 11,
            "mobile" : 4,
            "tablet" : 5,
        },
        "mobile_os": {
            "android": 4,
            "ios": 5,
            "window_phone": 0
        }
    },
    "segments" : [10,9,9,...],
    "duration": 242,
    "completion_rate": 0.42,
    "average_completion": 0.59,
    "countries": [
        { "name": "Sweden", "plays": 11},
        { "name": "Finland", "plays": 9}
    ],
    "domains": [
        { "name": "flowplayer.com", "plays": 11},
        { "name": "home.com", "plays": 9}
    ],
    "players": [
        { "name":"frontpage player", "id": "xyz", "plays": 11},
        { "name":"demo player", "id": "xyz", "plays": 9}
    ],
    "date_from": "2018-03-01T00:00:00.000Z",
    "date_to": "2018-03-08T00:00:00.000Z",
}
```

### HTTP Request

`GET https://api.flowplayer.com/analytics/category/:id`

### Request parameters

Parameter | Description
--------- | -------------------------------------
start     | optional, starting date/time of the interval, format `YYYY-MM-DDTHH` or `YYYY-MM-DD`
end       | optional, ending date/time of the interval, format `YYYY-MM-DDTHH` or `YYYY-MM-DD`

### Response parameters

Parameter | Description
--------- | -------------------------------------
displays        | number of displays for this Category. A `display` is registered when the player is completely loaded and ready to play the Category. 
plays.total    | total number of plays for this Category. A `play` is registered when the Category starts to play. If the Category have prerolls this is registered after all prerolls are complete.
plays.unique        | number of unique plays.
plays.device.desktop | number of plays on desktop
plays.device.mobile | number of plays on mobile
plays.device.tablet | number of plays on tablet
plays.mobile_os.android | number of plays on android
plays.mobile_os.ios | number of plays on ios
plays.mobile_os.windows_phone | number of plays on windows_phone
segments | number of viewers for each of the 100 segments of the videos for this Category.
completion_rate | Number of viewers that viewed until the end presented with a decimal value. E.g. 0.42 means that 42% of the viewers viewed until the end.
average_completion | How long the viewers viewed in average presented in decimal value. E.g. 0.5 means that the average user viewed 50% of the Category.
countries | List containing plays per country sorted with the country with highest number of plays first.
domains | List containing plays per domain sorted with the domain with highest number of plays first.
players | List containing plays per player sorted with the player with highest number of plays first.


## List Categories on Workspace

This endpoint returns categories having the most plays or displays on a Workspace during a specified period of time.

> Get the most played categories on a Workspace

``shell
curl "https://api.flowplayer.com/analytics/workspaces/<workspace_id>/categories" 
``

> 

```json
 [
        {
            "name": "Category 1",
            "id": "360b8f49-3c98-4020-ac72-83f958405239",
            "plays": 252863,
            "displays":1234020
        },
        {
            "name": "Category 2",
            "id": "3de6843f-2a65-46bd-a899-753d813f22c7",
            "plays": 227743,
            "displays":2131212
        },
        {
            "name": "Category 3",
            "id": "9242781d-149e-468c-bc80-b383bc6fd73d",
            "plays": 210430,
            "displays":523223
        },
        {
            "name": "Category 4",
            "id": "8ed589c1-9b88-4040-81f7-c063fcf139a2",
            "plays": 198156,
            "displays":234888
        },
        {
            "name": "Category 5",
            "id": "666f6532-8b6e-4ccf-84a0-0916ab827a24",
            "plays": 192380,
            "displays":766543
        },
        {
            "name": "Category 6",
            "id": "075d123a-8e58-4b05-b505-5f5ca8244a5d",
            "plays": 191079,
            "displays":237587
        },
        {
            "name": "Category 7",
            "id": "0548e44c-253a-4bb0-bf89-4f3d83b95dde",
            "plays": 189647,
            "displays":867655
        },
        {
            "name": "Category 8",
            "id": "6ebeec02-1f6c-45ef-a50e-eeaae4370da5",
            "plays": 184121,
            "displays":190001
        },
        {
            "name": "Category 9",
            "id": "89a371e5-da85-4160-a913-b82b9a0e6b4c",
            "plays": 181421,
            "displays":238800
        },
        {
            "name": "Category 10",
            "id": "bba4d3d9-ea9c-452f-83c3-e577c26a1784",
            "plays": 180103,
            "displays":188283
        }
]
```

> Get the most displays categories in a specific Workspace and in a specified time range, limiting the results to the top 3 categories.

```shell
curl "https://api.flowplayer.com/analytics/workspaces/categories/54af42d8-b41d-4efc-b355-38d879820184?size=3&start=2018-05-01&end=2018-05-31&sort=display"   
```

> Returns the three categories with most displays in Workspace `54af42d8-b41d-4efc-b355-38d879820184` during May 2018

```json
 [ 
    {
        "name": "Category 1",
        "id": "360b8f49-3c98-4020-ac72-83f958405239",
        "plays": 252863,       
        "displays":2131212
    },
    {
        "name": "Category 2",
        "id": "3de6843f-2a65-46bd-a899-753d813f22c7",
        "plays": 227743,
        "displays":1234020
    },
    {
        "name": "Category 3",
        "id": "9242781d-149e-468c-bc80-b383bc6fd73d",
        "plays": 210430,
        "displays":523223
    }
 ]
```

### HTTP Request

`GET https://api.flowplayer.com/analytics/workspaces/<workspace_id>/categories`

### Request parameters

Parameter | Description
--------- | -------------------------------------
id    | The Workspace's Id is mandatory in the path.
start     | optional, start date and time, format `YYY-MM-DDTHH` or `YYY-MM-DD`
end       | optional, end date and time, format `YYY-MM-DDTHH` or `YYY-MM-DD`
size      | optional, maximum number of categories to be returned, 10 is returned if size is not specified. The request is limited to return 100 categories.
sort      | optional, sorting used when listing the categories. Possible values `displays` and `plays`. The default value is `plays`.

## Get Organization summarized analytics

This endpoint is used to query summarized analytics for a specific Organization. 

The Organization completion series is divided into 100 `segments` and every `segment` represents 1% for average videos duration. The return value of this endpoint includes view counts for each of these 100 segments.

> Get analytics for Organization with Id 360b8f49-3c98-4020-ac72-83f958405239

```shell
curl "https://api.flowplayer.com/analytics/organizations/360b8f49-3c98-4020-ac72-83f958405239?start=2018-01-01&end=2018-12-04"
```


```json
{
    "display" : 100,
    "plays" : {
        "total" : 20,
        "unique": 10,
        "device" : {
            "desktop": 11,
            "mobile" : 4,
            "tablet" : 5,
        },
        "mobile_os": {
            "android": 4,
            "ios": 5,
            "window_phone": 0
        }
    },
    "segments" : [10,9,9,...],
    "duration": 242,
    "completion_rate": 0.42,
    "average_completion": 0.59,
    "countries": [
        { "name": "Sweden", "plays": 11},
        { "name": "Finland", "plays": 9}
    ],
    "domains": [
        { "name": "flowplayer.com", "plays": 11},
        { "name": "home.com", "plays": 9}
    ],
    "players": [
        { "name":"frontpage player", "id": "xyz", "plays": 11},
        { "name":"demo player", "id": "xyz", "plays": 9}
    ],
    "date_from": "2018-03-01T00:00:00.000Z",
    "date_to": "2018-03-08T00:00:00.000Z",
}
```

### HTTP Request

`GET https://api.flowplayer.com/analytics/organizations/:id`

### Request parameters

Parameter | Description
--------- | -------------------------------------
start     | optional, starting date/time of the interval, format `YYYY-MM-DDTHH` or `YYYY-MM-DD`
end       | optional, ending date/time of the interval, format `YYYY-MM-DDTHH` or `YYYY-MM-DD`

### Response parameters

Parameter | Description
--------- | -------------------------------------
displays        | number of displays for this Organization. A `display` is registered when the player is completely loaded and ready to play the Organization. 
plays.total    | total number of plays for this Organization. A `play` is registered when the Organization starts to play. If the Organization have prerolls this is registered after all prerolls are complete.
plays.unique        | number of unique plays.
plays.device.desktop | number of plays on desktop
plays.device.mobile | number of plays on mobile
plays.device.tablet | number of plays on tablet
plays.mobile_os.android | number of plays on android
plays.mobile_os.ios | number of plays on ios
plays.mobile_os.windows_phone | number of plays on windows_phone
segments | number of viewers for each of the 100 segments of the videos for this Organization.
completion_rate | Number of viewers that viewed until the end presented with a decimal value. E.g. 0.42 means that 42% of the viewers viewed until the end.
average_completion | How long the viewers viewed in average presented in decimal value. E.g. 0.5 means that the average user viewed 50% of the Organization.
countries | List containing plays per country sorted with the country with highest number of plays first.
domains | List containing plays per domain sorted with the domain with highest number of plays first.
players | List containing plays per player sorted with the player with highest number of plays first.


## List Workspaces on Organization

This endpoint returns workspaces having the most plays or displays on a Organization during a specified period of time.

> Get the most played workspaces on a Organization

``shell
curl "https://api.flowplayer.com/analytics/organizations/<organization_id>/workspaces" 
``

> 

```json
 [
        {
            "name": "Workspace 1",
            "id": "360b8f49-3c98-4020-ac72-83f958405239",
            "plays": 252863,
            "displays":1234020
        },
        {
            "name": "Workspace 2",
            "id": "3de6843f-2a65-46bd-a899-753d813f22c7",
            "plays": 227743,
            "displays":2131212
        },
        {
            "name": "Workspace 3",
            "id": "9242781d-149e-468c-bc80-b383bc6fd73d",
            "plays": 210430,
            "displays":523223
        },
        {
            "name": "Workspace 4",
            "id": "8ed589c1-9b88-4040-81f7-c063fcf139a2",
            "plays": 198156,
            "displays":234888
        },
        {
            "name": "Workspace 5",
            "id": "666f6532-8b6e-4ccf-84a0-0916ab827a24",
            "plays": 192380,
            "displays":766543
        },
        {
            "name": "Workspace 6",
            "id": "075d123a-8e58-4b05-b505-5f5ca8244a5d",
            "plays": 191079,
            "displays":237587
        },
        {
            "name": "Workspace 7",
            "id": "0548e44c-253a-4bb0-bf89-4f3d83b95dde",
            "plays": 189647,
            "displays":867655
        },
        {
            "name": "Workspace 8",
            "id": "6ebeec02-1f6c-45ef-a50e-eeaae4370da5",
            "plays": 184121,
            "displays":190001
        },
        {
            "name": "Workspace 9",
            "id": "89a371e5-da85-4160-a913-b82b9a0e6b4c",
            "plays": 181421,
            "displays":238800
        },
        {
            "name": "Workspace 10",
            "id": "bba4d3d9-ea9c-452f-83c3-e577c26a1784",
            "plays": 180103,
            "displays":188283
        }
]
```

> Get the most displays workspaces in a specific Organization and in a specified time range, limiting the results to the top 3 workspaces.

```shell
curl "https://api.flowplayer.com/analytics/organizations/54af42d8-b41d-4efc-b355-38d879820184/workspaces?size=3&start=2018-05-01&end=2018-05-31&sort=display"   
```

> Returns the three workspaces with most displays in Organization `54af42d8-b41d-4efc-b355-38d879820184` during May 2018

```json
 [ 
    {
        "name": "Workspace 1",
        "id": "360b8f49-3c98-4020-ac72-83f958405239",
        "plays": 252863,       
        "displays":2131212
    },
    {
        "name": "Workspace 2",
        "id": "3de6843f-2a65-46bd-a899-753d813f22c7",
        "plays": 227743,
        "displays":1234020
    },
    {
        "name": "Workspace 3",
        "id": "9242781d-149e-468c-bc80-b383bc6fd73d",
        "plays": 210430,
        "displays":523223
    }
 ]
```

### HTTP Request

`GET https://api.flowplayer.com/analytics/organizations/<organization_id>/workspaces`

### Request parameters

Parameter | Description
--------- | -------------------------------------
id    | The Organization's Id is mandatory in the path, this also sometimes also referred to as SiteGroup id.
start     | optional, start date and time, format `YYY-MM-DDTHH` or `YYY-MM-DD`
end       | optional, end date and time, format `YYY-MM-DDTHH` or `YYY-MM-DD`
size      | optional, maximum number of workspaces to be returned, 10 is returned if size is not specified. The request is limited to return 200 workspaces.
sort      | optional, sorting used when listing the workspaces. Possible values `displays` and `plays`. The default value is `plays`.


## Get Player Configuration timeseries analytics

This endpoint returns plays counts for specified time intervals.

> Get timeseries data

```shell
curl "https://api.flowplayer.com/analytics/players/<configuration_id>/timeseries?start=2018-10-31&end=2018-11-20" 
```

> Returns following:

```json
{
    "series": {
        "date_from": "2018-10-31T00:00:00.000Z",
        "date_to": "2018-11-20T00:00:00.000Z",
        "intervals": [{
            "time": "2018-10-31T00:00:00.000Z",
            "plays": 10,
        },{
            "time": "2018-11-01T00:00:00.000Z",
            "plays": 20,
        },{
            "time": "2018-11-02T00:00:00.000Z",
            "plays": 30,
        },
        ....
        ],
        "total": {
            "plays": 60
        }
    }
}
```

### HTTP Request

`GET https://api.flowplayer.com/analytics/players/<configuration_id>/timeseries`

### Request parameters

Parameter | Description
--------- | -------------------------------------
start     | optional - start date and time, format `YYYY-MM-DDTHH` or `YYYY-MM-DD`. If not specified it will return analytics for the last seven days in daily interval.
end       | optional - end date and time, format `YYYY-MM-DDTHH` or `YYYY-MM-DD`

### Response parameters

Parameter | Description
--------- | -------------------------------------

## List Videos for Player Configuration

This endpoint returns videos having the most plays using a Player Configuration during a specified period of time.

> Get the most played videos on a Player Configuration

``shell
curl "https://api.flowplayer.com/analytics/players/<configuration_id>/videos" 
``

> 

```json
 [
        {
            "name": "Video 1",
            "id": "360b8f49-3c98-4020-ac72-83f958405239",
            "plays": 252863
        },
        {
            "name": "Video 2",
            "id": "3de6843f-2a65-46bd-a899-753d813f22c7",
            "plays": 227743
        },
        {
            "name": "Video 3",
            "id": "9242781d-149e-468c-bc80-b383bc6fd73d",
            "plays": 210430
        },
        {
            "name": "Video 4",
            "id": "8ed589c1-9b88-4040-81f7-c063fcf139a2",
            "plays": 198156
        },
        {
            "name": "Video 5",
            "id": "666f6532-8b6e-4ccf-84a0-0916ab827a24",
            "plays": 192380
        },
        {
            "name": "Video 6",
            "id": "075d123a-8e58-4b05-b505-5f5ca8244a5d",
            "plays": 191079
        },
        ...
]
```


### HTTP Request

`GET https://api.flowplayer.com/analytics/players/<configuration_id>/videos`

### Request parameters

Parameter | Description
--------- | -------------------------------------
id    | The Player Configuration's Id is mandatory in the path,.
start     | optional, start date and time, format `YYY-MM-DDTHH` or `YYY-MM-DD`
end       | optional, end date and time, format `YYY-MM-DDTHH` or `YYY-MM-DD`
size      | optional, maximum number of videos to be returned, 10 is returned if size is not specified. The request is limited to return 200 videos.


## List Livestreams for Player Configuration

This endpoint returns livestreams having the most plays using a Player Configuration during a specified period of time.

> Get the most played livestreams on a Player Configuration

``shell
curl "https://api.flowplayer.com/analytics/players/<configuration_id>/livestreams" 
``

> 

```json
 [
        {
            "name": "Livestream 1",
            "id": "360b8f49-3c98-4020-ac72-83f958405239",
            "plays": 252863
        },
        {
            "name": "Livestream 2",
            "id": "3de6843f-2a65-46bd-a899-753d813f22c7",
            "plays": 227743
        },
        {
            "name": "Livestream 3",
            "id": "9242781d-149e-468c-bc80-b383bc6fd73d",
            "plays": 210430
        },
        {
            "name": "Livestream 4",
            "id": "8ed589c1-9b88-4040-81f7-c063fcf139a2",
            "plays": 198156
        },
        {
            "name": "Livestream 5",
            "id": "666f6532-8b6e-4ccf-84a0-0916ab827a24",
            "plays": 192380
        },
        {
            "name": "Livestream 6",
            "id": "075d123a-8e58-4b05-b505-5f5ca8244a5d",
            "plays": 191079
        },
        ...
]
```


### HTTP Request

`GET https://api.flowplayer.com/analytics/players/<configuration_id>/livestreams`

### Request parameters

Parameter | Description
--------- | -------------------------------------
id    | The Player Configuration's Id is mandatory in the path,.
start     | optional, start date and time, format `YYY-MM-DDTHH` or `YYY-MM-DD`
end       | optional, end date and time, format `YYY-MM-DDTHH` or `YYY-MM-DD`
size      | optional, maximum number of livestreams to be returned, 10 is returned if size is not specified. The request is limited to return 200 livestreams.

