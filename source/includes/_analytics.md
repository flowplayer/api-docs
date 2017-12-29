# Analytics for VOD

## Get analytics for a specific video

This endpoint is used to query anlytics for a specific video. It returns view and display counts and segments view counts.
A `view` is counted when playback starts and a `display` happens when the video player is shown for this video.

The video timeline is divided into 100 `segments`. The return value of this endpoint includes view counts for each of 
these 100 segments.

> Get analytics for video with ID 360b8f49-3c98-4020-ac72-83f958405239

```shell
curl "https://api.flowplayer.com/analytics/videos/360b8f49-3c98-4020-ac72-83f958405239?start=2017-12-01&end=2017-12-04"
```

> Returns display and view counts, and segments statistics as follows

```json
{ "displayViews": 
   { "display": 109667,
     "view": 86886,
     "views_desk": -1,
     "views_mob": -1,
     "views_tab": -1,
     "views_os_mob_android": -1,
     "views_os_mob_ios": -1,
     "views_os_mob_winph": -1 },
     "segments":[86048,19772,14731,12245,10657,9521,8726,8010,7473,6977,6562,6261,5973,5719,5521,5314,5135,4968,4833,4711,4590,4481,4382,4287,4190,4105,4021,3946,3882,3821,3762,3691,3638,3600,3561,3523,3480,3442,3407,3363,3313,3277,3232,3197,3172,3152,3120,3086,3053,3028,3006,2983,2957,2937,2913,2884,2863,2835,2812,2787,2765,2740,2725,2698,2672,2650,2629,2609,2585,2580,2562,2541,2527,2513,2499,2484,2462,2446,2428,2416,2400,2386,2381,2366,2349,2327,2318,2299,2282,2273,2266,2250,2242,2231,2216,2203,2191,2174,2160,2146]
}
```

### HTTP Request

`GET https://api.flowplayer.com/analytics/videos/:id`

### Request parameters

Parameter | Description
--------- | -------------------------------------
start     | Optional starting date/time of the interval, format `YYY-MM-DDTHH` or `YYY-MM-DD`
end       | optional ending date/time of the interval, format `YYY-MM-DDTHH` or `YYY-MM-DD`


## Current number of viewers

This endpoint returns the current viewer count matching the specified parameters.

> Get current number of viewers for all videos belonging to the site group 

```shell
curl "https://api.flowplayer.com/analytics/viewers" 
```

> returns the the estimated number of viewers

```json
{"viewers":250}
```

> Get current number of viewers for one video 

```shell
curl "https://api.flowplayer.com/analytics/viewers?id=360b8f49-3c98-4020-ac72-83f958405239" 
```

> Get current number of viewers for two videos 

```shell
curl "https://api.flowplayer.com/analytics/viewers?id=[360b8f49-3c98-4020-ac72-83f958405239,00048d7e-7ffb-46ee-ae21-e49b3668fea8]" 
```

### HTTP Request

`GET https://api.flowplayer.com/analytics/viewers`

### Request parameters

The query can be restricted to one or more videos, and/or to one or more sites. The query will match all videos in all sites
in the account's site group, if no `site` not `id` is passed as a parameter. 

Parameter | Description
--------- | -------------------------------------
id        | optional video ID, or a list of several IDs 
siteId    | optional site ID, or a list of site IDs

### Errors

HTTP status | Description
----------- | --------------------------------------------
404         | if the specified site or video is not found

## Videos with viewers

This endpoint returns the top videos having viewers at the moment. Maximum 100 videos will be returned, and the amount
is less than this if fewer videos have viewers.

> Get videos with most viewers

```shell
curl "https://api.flowplayer.com/analytics/viewers/videos"
```

> Returns a list of videos in decreasing `viewers` count.

```json
[
    	{
    		"siteId": "54af42d8-b41d-4efc-b355-38d879820184",
    		"id": "60842d37-8e2f-4709-bacf-aebf6e4d9299",
    		"viewers": 31
    	},
    	{
    		"siteId": "54af42d8-b41d-4efc-b355-38d879820184",
    		"id": "f1e38ef5-a98c-41d5-81cb-523bf0f2fa59",
    		"viewers": 27
    	},
    	{
    		"siteId": "54af42d8-b41d-4efc-b355-38d879820184",
    		"id": "6ebeec02-1f6c-45ef-a50e-eeaae4370da5",
    		"viewers": 24
    	},
    	{
    		"siteId": "54af42d8-b41d-4efc-b355-38d879820184",
    		"id": "89a371e5-da85-4160-a913-b82b9a0e6b4c",
    		"viewers": 23
    	}
]
```

### HTTP Request

`GET https://api.flowplayer.com/analytics/viewers/videos`


> Get videos with most viewers for a specific site

```shell
curl "https://api.flowplayer.com/analytics/viewers/videos?siteId=54af42d8-b41d-4efc-b355-38d879820184"
```

### Request parameters

Parameter | Description
--------- | -------------------------------------
id        | optional video ID, or a list of several IDs 
siteId    | optional site ID, or a list of site IDs

## Intervals

This endpoint returns view and display counts for specified time intervals.

> Get data for today, with a comparison to yesterday.

```shell
curl "https://api.flowplayer.com/analytics/intervals" 
```

> Returns an array with two entries: One for today and one for yesterday. On 2017-12-19 it returned following:

```json
[
    	{
    		"date_from": "2017-12-17T11:00:00.000Z",
    		"date_to": "2017-12-18T11:00:00.000Z",
    		"intervals": [
    			{
    				"time": "2017-12-18T11:00:00.000Z",
    				"views": 69055,
    				"displays": 108993
    			}
    		],
    		"total": {
    			"displays": 108993,
    			"views": 69055
    		}
    	},
    	{
    		"date_from": "2017-12-18T11:00:00.000Z",
    		"date_to": "2017-12-19T11:00:00.000Z",
    		"intervals": [
    			{
    				"time": "2017-12-19T11:00:00.000Z",
    				"views": 137152,
    				"displays": 212893
    			}
    		],
    		"total": {
    			"displays": 212893,
    			"views": 137152
    		}
    	}
    ]
```

> Get hourly stats for three hours, comparing them to the previous three hours.

```shell
curl "https://api.flowplayer.com/analytics/intervals?start=2017-12-01T00&end=2017-12-01T03"
```

> Returns two intervals, one for the queried time range between 2017-12-01T00 and end=2017-12-01T03, and another interval
is automatically added for a second three hour segment before the queried start time

```json
 [
    	{
    		"date_from": "2017-11-30T20:00:00.000Z",
    		"date_to": "2017-12-01T00:00:00.000Z",
    		"intervals": [
    			{
    				"time": "2017-11-30T21:00:00.000Z",
    				"views": 16522,
    				"displays": 24612
    			},
    			{
    				"time": "2017-11-30T22:00:00.000Z",
    				"views": 4832,
    				"displays": 7162
    			},
    			{
    				"time": "2017-11-30T23:00:00.000Z",
    				"views": 2002,
    				"displays": 3531
    			},
    			{
    				"time": "2017-12-01T00:00:00.000Z",
    				"views": 0,
    				"displays": 0
    			}
    		],
    		"total": {
    			"displays": 35305,
    			"views": 23356
    		}
    	},
    	{
    		"date_from": "2017-12-01T00:00:00.000Z",
    		"date_to": "2017-12-01T03:00:00.000Z",
    		"intervals": [
    			{
    				"time": "2017-12-01T01:00:00.000Z",
    				"views": 1507,
    				"displays": 2684
    			},
    			{
    				"time": "2017-12-01T02:00:00.000Z",
    				"views": 244,
    				"displays": 439
    			},
    			{
    				"time": "2017-12-01T03:00:00.000Z",
    				"views": 0,
    				"displays": 0
    			}
    		],
    		"total": {
    			"displays": 3123,
    			"views": 1751
    		}
    	}
    ]
```

> To exclude the automatically added previous time range, specify `previous=false`.

```shell
curl "https://api.flowplayer.com/analytics/intervals?start=2017-12-01&end=2017-12-17&previous=false"
```

### HTTP Request

`GET https://api.flowplayer.com/analytics/intervals`

### Request parameters

The query can be restricted to one or more videos, and/or to one or more sites. The query will match all videos in all sites
in the account's site group, if no `site` not `id` is passed as a parameter. 

Parameter | Description
--------- | -------------------------------------
id        | optional video ID, or a list of several IDs 
siteId    | optional site ID, or a list of site IDs
start     | optional start date and time, format `YYY-MM-DDTHH` or `YYY-MM-DD`
end       | optional end date and time, format `YYY-MM-DDTHH` or `YYY-MM-DD`


## Popular videos

This endpoint returns videos having the largest amount of views.

> Get the most popular videos

```shell
curl "https://api.flowplayer.com/analytics/views" 
```

> Returns the IDs and view counts of the 10 most popular videos

```json
 [
    	{
    		"id": "360b8f49-3c98-4020-ac72-83f958405239",
    		"views": 252863
    	},
    	{
    		"id": "3de6843f-2a65-46bd-a899-753d813f22c7",
    		"views": 227743
    	},
    	{
    		"id": "9242781d-149e-468c-bc80-b383bc6fd73d",
    		"views": 210430
    	},
    	{
    		"id": "8ed589c1-9b88-4040-81f7-c063fcf139a2",
    		"views": 198156
    	},
    	{
    		"id": "666f6532-8b6e-4ccf-84a0-0916ab827a24",
    		"views": 192380
    	},
    	{
    		"id": "075d123a-8e58-4b05-b505-5f5ca8244a5d",
    		"views": 191079
    	},
    	{
    		"id": "0548e44c-253a-4bb0-bf89-4f3d83b95dde",
    		"views": 189647
    	},
    	{
    		"id": "6ebeec02-1f6c-45ef-a50e-eeaae4370da5",
    		"views": 184121
    	},
    	{
    		"id": "89a371e5-da85-4160-a913-b82b9a0e6b4c",
    		"views": 181421
    	},
    	{
    		"id": "bba4d3d9-ea9c-452f-83c3-e577c26a1784",
    		"views": 180103
    	}
]
```

> Get the most popular videos in a specific site and in a specified time range, limiting the results to the top 3 videos.

```shell
curl "https://api.flowplayer.com/analytics/views?siteId=54af42d8-b41d-4efc-b355-38d879820184&size=3&start=2017-12-01&end=2017-12-31"   
```

> Returns the three videos with most views in site `54af42d8-b41d-4efc-b355-38d879820184` during December 2017

```json
 [
    	{
    		"id": "360b8f49-3c98-4020-ac72-83f958405239",
    		"views": 178606
    	},
    	{
    		"id": "6ebeec02-1f6c-45ef-a50e-eeaae4370da5",
    		"views": 160528
    	},
    	{
    		"id": "89a371e5-da85-4160-a913-b82b9a0e6b4c",
    		"views": 157764
    	}
 ]
```

### HTTP Request

`GET https://api.flowplayer.com/analytics/views`

### Request parameters

The query can be restricted to one or more videos, and/or to one or more sites. The query will match all videos in all sites
in the account's site group, if no `site` not `id` is passed as a parameter. 

Parameter | Description
--------- | -------------------------------------
id        | optional video ID, or a list of several IDs 
siteId    | optional site ID, or a list of site IDs
start     | optional start date and time, format `YYY-MM-DDTHH` or `YYY-MM-DD`
end       | optional end date and time, format `YYY-MM-DDTHH` or `YYY-MM-DD`


# Analytics for live broadcasts

## Currently running live casts

This endpoint returns the viewer counts of all broadcasts that are current live and public.

> Get current live viewer counts

```shell
curl "https://api.flowplayer.com/analytics/live"
```

> returns all livecasts that currently have viewers

```bash
 [
    	{
    		"siteId": "e426f62e-c59c-4820-a3e2-83e33a79f65d",
    		"id": "a84c6ba2-54cb-4e09-bfb8-20eb9f68c814",
    		"views": 587
    	},
    	{
    		"siteId": "b8bb09c1-fa63-4702-a3e5-bb4107f3344e",
    		"id": "a8f90631-da13-4959-be0a-f2cde9ea9196",
    		"views": 144
    	},
    	{
    		"siteId": "7f4d50f9-7a1a-4e89-aa19-5bcd8ea8bf2e",
    		"id": "22f7356a-515c-4842-af87-cbbe117c9a8d",
    		"views": 24
    	}
    ]
```


### HTTP Request

`GET https://api.flowplayer.com/analytics/live`

### Request parameters

The query can be restricted to one or more videos, and/or to one or more sites. The query will match all videos in all sites
in the account's site group, if no `site` not `id` is passed as a parameter. 

Parameter | Description
--------- | -------------------------------------
id        | optional live ID, or a list of several IDs 
siteId    | optional site ID, or a list of site IDs
