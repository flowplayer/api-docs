# Video analytics (VOD)

## Get analytics for a specific video

This endpoint is used to query anlytics for a specific video. It returns view and display counts and segments view counts.
A `view` is counted when playback starts and a `display` happens when the video player is shown for this video.

The video timeline is divided into 100 `segments`. The return value of this endpoint includes view counts for each of 
these 100 segments.

> Get analytics for video with ID 360b8f49-3c98-4020-ac72-83f958405239

```shell
curl "https://api.flowplayer.com/videos/360b8f49-3c98-4020-ac72-83f958405239" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -d $'{
  "end": "2017-12-31T00",
  "start": "2017-12-01T00"
}'
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

`GET https://api.flowplayer.com/videos/:id`

### Request parameters

Parameter | Description
--------- | -------------------------------------
start     | Optional starting date/time of the interval, format `YYY-MM-DDTHH` or `YYY-MM-DD`
end       | optional ending date/time of the interval, format `YYY-MM-DDTHH` or `YYY-MM-DD`


## Current viewers

This endpoint returns the current view count matching the specified parameters.

> Get current number of viewers for all videos belonging to the site group 

```shell
curl "https://api.flowplayer.com/current" 
```

> returns the the estimated number of viewers

```json
{"views":250}
```

> Get current number of viewers for one video 

```shell
curl "https://api.flowplayer.com/current?id=360b8f49-3c98-4020-ac72-83f958405239" 
```

> Get current number of viewers for two videos 

```shell
curl "https://api.flowplayer.com/current?id=[360b8f49-3c98-4020-ac72-83f958405239,00048d7e-7ffb-46ee-ae21-e49b3668fea8]" 
```

### HTTP Request

`/videos/:id/current`

### Request parameters

The query can be restricted to one or more videos, and/or to one or more sites. The query will match all videos in all sites
in the account's site group, if no `site` not `id` is passed as a parameter. 

Parameter | Description
--------- | -------------------------------------
id        | optional video ID, or a list of several IDs 
site      | optional site ID, or a list of site IDs

### Errors

HTTP status | Description
----------- | --------------------------------------------
404         | if the specified site or video is not found

