# Playlists

## Get Playlist (NOT IMPLEMENTED)

Endpoint for fetching infomation about one single playlist

> Endpoint for fetching infomation about one single playlist

```shell
curl "https://api.flowplayer.com/playlists/{playlist_id}"
```

```json
{
    TBD
}
```

### HTTP Request

`GET https://api.flowplayer.com/playlists/:playlist_id`


### Request parameters

### Response

Parameter | Description
--------- | -------------------------------------

### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified Playlist is not found


## List Playlists (NOT IMPLEMENTED)

Endpoint for fetching infomation about playlists on a specific Site. The response is list of livecasts and for each livecast it contains a subset of the information available in the `get livecast`-request.

> Endpoint for fetching infomation about livecasts on a specific Site.

```shell
curl "https://api.flowplayer.com/playlists?siteId={site_id}"
```

```json
{
    "total_count": 21,
    "total_count_in_search": 1,
    "page": 0,
    "page_size": 20,
    "total_pages": 1,
    "assets": [
        {
            TBD
        }
    ]
}
```



### HTTP Request

`GET https://api.flowplayer.com/playlists?siteId={site_id}`


### Request parameters

Parameter | Description
--------- | -------------------------------------
siteId        | The site for which it lists the playlists.
page        | `optional` - Page for response, default value is `0`.
pageSize        | `optional` - Page size for response, default value is `20`.
search | `optional` - Search term for filtering the response. Searches `name`.
sortBy | `optional` - Sorting column for the response, default value is `created_at`. Possible values: `created_at`, `name`.
sortOrder | `optional` - Sorting order for the response, default value is `desc`. Possible values `asc` and `desc`
filter | `optional` - TBD

### Response

Parameter | Description
--------- | -------------------------------------
TBD

### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified Site or Livecast is not found


## Create Playlist (EXISTING, BUT TO REWRITE)

Endpoint for creating a playlist

> Endpoint for creating a playlist

```shell
curl "https://web.lemonwhale.com/web/video/v2/playlist/create.json"
```

```json
{
    "name": "Flowplayer Livcast",
    "api_key":"xyz",
    "continue_play":true,
    "videos":["videoId_1","videoId_2"]
}
```

### HTTP Request

`POST https://web.lemonwhale.com/web/video/v2/playlist/create.json`


### Request parameters

Parameter | Description
--------- | -------------------------------------
name      | Name of the playlist
api_key      | `optional` - Page for response, default value is `0`.
continue_play      | `optional` - Should the list automatically continue to play the next video. Default `false`.
videos | A list of video ids to include in the list

### Response

Parameter | Description
--------- | -------------------------------------
id      | Id of the playlist
name      | Name of the playlist
site_id      | 
continue_play      | Should the list automatically continue to play the next video.
random_order      | Boolean which describs ff the player should shuffle the videos in the list.
created_at      | 
updated_at      | 
video_count | Number of videos in playlist
video | List of all videos in playlist

## Update Playlist (NOT IMPLEMENTED)

### HTTP Request



### Request parameters

Parameter | Description
--------- | -------------------------------------
TBD

### Response

Parameter | Description
--------- | -------------------------------------
TDB

## Delete Playlist (NOT IMPLEMENTED)

Endpoint for deleting one single playlist


### HTTP Request

`DELETE `

### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified Playlist is not found
