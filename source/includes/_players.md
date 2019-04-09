# Players

## Get Player

Endpoint for fetching a configuration for one single player

> Endpoint for fetching a configuration for one single player

```shell
curl "https://app.flowplayer.com/ovp/workspaces/:workspace_id/player-config/:player_id"
```

```json
{
    "id": ":player_id",
    "name": "Player Configuration 1",
    "created_at": "2019-04-04T10:26:09+0000",
    "updated_at": "2019-04-04T10:26:09+0000",
    "ad_schedule": {
        "id": ":ad_schedule_id",
        "name": "AdOne",
        "type": "VAST",
        "created": "2019-02-26T14:59:52+0000",
        "updated": "2019-02-26T14:59:52+0000",
        "breaks": []
    },
    "responsive": true,
    "height": 360,
    "width": 640,
    "logo": {},
    "autoplay": false,
    "muted": false,
    "cast": true,
    "appearance": {
        "brand_color": "1d97c2",
        "controls": true,
        "fullscreen": true,
        "volume": true,
        "playback_rate": false,
        "quality": false
    },
    "recommendations": {
        "advance": false,
        "interval": 0,
        "source":"playlist"
    },
    "recommendation_playlist": {
        "id": ":playlist_id",
        "name": "Playlist",
        "created": "2018-03-13T21:16:12+0000",
        "updated": "2018-11-25T09:47:24+0000",
        "playlist_type": "MANUAL"
    },
		"skin": {
			"name": "Standard"
		},
    "language": {
        "name": "ENG"
    },
    "default_quality": "HIGH",
    "preload": "METADATA",
    "version": "NATIVE",
    "release_channel": "STABLE",
    "loop": false
}
```

### HTTP Request

`GET https://app.flowplayer.com/ovp/workspaces/:workspace_id/player-config/:player_id`


### Request parameters

### Response

Parameter | Description
--------- | -------------------------------------
id        | The player id used in embed codes to identify the player
name      | The player name
created_at | The creation date formatted in `yyyy-MM-dd'T'HH:mm:ssZ`.
updated_at | The latest update formatted in `yyyy-MM-dd'T'HH:mm:ssZ`.
ad_schedule.id | The platform ad schedule connected to this player. The player will use this ad schedules configuration to request ads.
responsive | If the player by default should be presented as responsive
height | In case the player is not set as `responsive` this property is used to set the height of the player in pixels
width | In case the player is not set as `responsive` this property is used to set the width of the player in pixels
logo[] | An array containing all logos that should be rendered on the player
logo[].src | Url to the logo image
logo[].position | Position in the player for the logo. Possible values are `left` or `right` and depending on the value the logo will be places in either the upper left or upper right corner.
autoplay | If the player should auto start.
muted | If the player should start muted
loop | If the player should loop the content
cast | If the player should have `Chromecast` and `Airplay` support
skin | Contains the name of the skin in use. Different values depending on the player's version
appearance | Content of appearance depends on the version of the player.
appearance.brand_color | Supported in both `Native` and  `7`. Sets the color of for example the progress bar.
appearance.controls | Supported in both `Native` and  `7`. If controls should be visible in player.
appearance.show_title | Supported in both `Native` and  `7`. If the media asset title should be visible in player.
appearance.show_description | Supported in both `Native` and  `7`. If the media asset description should be visible in player.
appearance.fullscreen | Supported in both `Native` and  `7`. If fullscreen button and functionality is available in player.
appearance.volume | Supported in both `Native` and  `7`. If volume button is available in player.
appearance.playback_rate | Supported in both `Native` and  `7`. If playback rate button is available in player.
appearance.quality | Supported in both `Native` and  `7`. If quality selection button is available in player.
appearance.outlined | Supported in `7`. If `outlined` style is used in player.
appearance.rounded | Supported in `7`. If `rounded` style is used in player.
share | Contains the configuration of the Social Sharing plugin
share.embed | Supported in both `Native` and  `7`. If embed options is available in Share screen.
share.link | Supported in both `Native` and  `7`. If link options is available in Share screen.
share.facebook | Supported in both `Native` and  `7`. If facebook options is available in Share screen.
share.twitter | Supported in both `Native` and  `7`. If twitter options is available in Share screen.
share.share_type | Supported in both `Native` and  `7`. Determines what should be shared in the different options. Possible values `PLAYER` or `PARENT`, where `PARENT` will share the page where the player is embedded and `PLAYER` will share the Iframe if player is embedded with Platform Iframe-embed.
recommendations | Settings for how to rendered recommendations.
recommendations.advance | If `true` it will automatically start playing the next video.
recommendations.interval | Determines the wait time until next video automatically will start playing.
recommendations.source | Determines with type of content to be display in the recommendations screen. We have three different possible value `none`, `playlist` and `dynamic`. No recommendations will be displayed if `none` is set. With `dynamic` the platform will automatically fill the recommendation screen with videos related to the displayed video. For `playlist` it will use the playlist specified in `recommendation_playlist` to fetch videos. By default `dynamic` will be used.
recommendation_playlist | The playlist, if any, that will be used to fetch videos to the recommendations screen.
recommendation_playlist | The playlist, if any, that will be used to fetch videos to the recommendations screen.
restrictions | An array containing host where the player is allowed to render.
language | Language used in the player. Possible values: TODO
default_quality | Starting quality used to fetch the first segments of HLS streams. Possible values `LOW`, `MEDIUM`, `HIGH`.
preload | Preloading setting that determines how the player should handle video data loading before play. Possible values `NONE`, `METADATA`, `AUTO`.
version | Player version used by this player. Possible values `VIDEO_JS`, `FLOWPLAYER_7`, `NATIVE`.
release_channel | To use either `EDGE` or  `STABLE` version of `Native` player. This property is only supported by `Native` version.


### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified Workspace or player is not found


## List Players

Endpoint for fetching players on a specific Workspace. The response is list of players.

> Endpoint for fetching players on a specific Workspace.

```shell
curl "https://app.flowplayer.com/ovp/workspaces/:workspace_id/player-configs"
```

```json
{
	"query": null,
	"total_count": 2,
	"total_count_in_search": 2,
	"page": 0,
	"page_size": 20,
	"total_pages": 1,
	"search_term": "",
	"assets": [{
		"id": "fbb7fb52-b704-4cc8-9e8c-b23b6827a339",
		"name": "VMAP Player",
		"created_at": "2018-08-20T10:17:23+0000",
		"updated_at": "2018-08-20T10:17:23+0000",
		"responsive": true,
		"height": 270,
		"width": 480,
		"autoplay": false,
		"muted": false,
		"cast": true,
		"appearance": {
			"brand_color": "4d4d4d",
			"controls": true,
			"fullscreen": true,
			"volume": true,
			"playback_rate": false,
			"quality": true
		},
		"skin": {
			"name": "Standard"
		},
		"share": {},
		"restrictions": [],
		"language": {
			"name": "ENG"
		},
		"default_quality": "LOW",
		"preload": "METADATA",
		"version": "FLOWPLAYER_7",
		"release_channel": "STABLE",
		"loop": false
	}, {
		"id": "76591990-b472-49d8-a467-c1199a8820bb",
		"name": "Trial Default",
		"created_at": "2017-12-15T07:50:35+0000",
		"updated_at": "2019-04-04T10:42:15+0000",
		"responsive": true,
		"height": 360,
		"width": 640,
		"autoplay": false,
		"muted": false,
		"cast": true,
		"appearance": {
			"outlined": true,
			"rounded": true,
			"show_description": true,
			"show_title": true,
			"brand_color": "ffff22",
			"controls": true,
			"fullscreen": true,
			"volume": true,
			"quality": true
		},
		"skin": {
			"name": "Magazine"
		},
		"share": {
			"embed": true,
			"link": true,
			"facebook": true,
			"twitter": true,
			"share_type": ""
		},
		"recommendations": {
			"advance": false,
			"interval": 0,
      "source":"none"
		},
		"restrictions": ["flowplayer.com", "google.com"],
		"language": {
			"name": "ENG"
		},
		"default_quality": "MEDIUM",
		"preload": "METADATA",
		"version": "FLOWPLAYER_7",
		"release_channel": "STABLE",
		"loop": false
	}]
}
```



### HTTP Request

`GET https://app.flowplayer.com/ovp/workspaces/:workspace_id/player-configs`


### Request parameters

Parameter | Description
--------- | -------------------------------------
page        | `optional` - Page for response, default value is `0`.
page_size        | `optional` - Page size for response, default value is `20`.
search | `optional` - Search term for filtering the response. Searches `name` and `id`.
sort_by | `optional` - Sorting column for the response, default value is `created_at`. Possible values: `created_at`, `name`.
sort_order | `optional` - Sorting order for the response, default value is `desc`. Possible values `asc` and `desc`

### Response

Parameter | Description
--------- | -------------------------------------
id        | The player id used in embed codes to identify the player
name      | The player name
created_at | The creation date formatted in `yyyy-MM-dd'T'HH:mm:ssZ`.
updated_at | The latest update formatted in `yyyy-MM-dd'T'HH:mm:ssZ`.
ad_schedule | The platform ad schedule connected to this player. The player will use this ad schedules configuration to request ads.
responsive | If the player by default should be presented as responsive
height | In case the player is not set as `responsive` this property is used to set the height of the player in pixels
width | In case the player is not set as `responsive` this property is used to set the width of the player in pixels
logo[] | An array containing all logos that should be rendered on the player
logo[].src | Url to the logo image
logo[].position | Position in the player for the logo. Possible values are `left` or `right` and depending on the value the logo will be places in either the upper left or upper right corner.
autoplay | If the player should auto start.
muted | If the player should start muted
loop | If the player should loop the content
cast | If the player should have `Chromecast` and `Airplay` support
skin | Contains the name of the skin in use. Different values depending on the player's version
appearance | Content of appearance depends on the version of the player.
appearance.brand_color | Supported in both `Native` and  `7`. Sets the color of for example the progress bar.
appearance.controls | Supported in both `Native` and  `7`. If controls should be visible in player.
appearance.show_title | Supported in both `Native` and  `7`. If the media asset title should be visible in player.
appearance.show_description | Supported in both `Native` and  `7`. If the media asset description should be visible in player.
appearance.fullscreen | Supported in both `Native` and  `7`. If fullscreen button and functionality is available in player.
appearance.volume | Supported in both `Native` and  `7`. If volume button is available in player.
appearance.playback_rate | Supported in both `Native` and  `7`. If playback rate button is available in player.
appearance.quality | Supported in both `Native` and  `7`. If quality selection button is available in player.
appearance.outlined | Supported in `7`. If `outlined` style is used in player.
appearance.rounded | Supported in `7`. If `rounded` style is used in player.
share | Contains the configuration of the Social Sharing plugin
share.embed | Supported in both `Native` and  `7`. If embed options is available in Share screen.
share.link | Supported in both `Native` and  `7`. If link options is available in Share screen.
share.facebook | Supported in both `Native` and  `7`. If facebook options is available in Share screen.
share.twitter | Supported in both `Native` and  `7`. If twitter options is available in Share screen.
share.share_type | Supported in both `Native` and  `7`. Determines what should be shared in the different options. Possible values `PLAYER` or `PARENT`, where `PARENT` will share the page where the player is embedded and `PLAYER` will share the Iframe if player is embedded with Platform Iframe-embed.
recommendations | Settings for how to rendered recommendations.
recommendations.advance | If `true` it will automatically start playing the next video.
recommendations.interval | Determines the wait time until next video automatically will start playing.
recommendations.source | Determines with type of content to be display in the recommendations screen. We have three different possible value `none`, `playlist` and `dynamic`. No recommendations will be displayed if `none` is set. With `dynamic` the platform will automatically fill the recommendation screen with videos related to the displayed video. For `playlist` it will use the playlist specified in `recommendation_playlist` to fetch videos. By default `dynamic` will be used.
recommendation_playlist | The playlist, if any, that will be used to fetch videos to the recommendations screen.
restrictions | An array containing host where the player is allowed to render.
language | Language used in the player. Possible values: TODO
default_quality | Starting quality used to fetch the first segments of HLS streams. Possible values `LOW`, `MEDIUM`, `HIGH`.
preload | Preloading setting that determines how the player should handle video data loading before play. Possible values `NONE`, `METADATA`, `AUTO`.
version | Player version used by this player. Possible values `VIDEO_JS`, `FLOWPLAYER_7`, `NATIVE`.
release_channel | To use either `EDGE` or  `STABLE` version of `Native` player. This property is only supported by `Native` version.

### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified Workspace is not found


## Create Player

Endpoint for creating a player

> Endpoint for creating a player

```shell
curl "https://app.flowplayer.com/ovp/workspaces/:workspace_id/player-config"
```

```json
{
  "name": "Demo Trial Default",
  "responsive": true,
  "height": 360,
  "width": 640,
  "autoplay": false,
  "muted": false,
  "cast": true,
  "appearance": {
    "outlined": true,
    "rounded": true,
    "show_description": true,
    "show_title": true,
    "brand_color": "ffff22",
    "controls": true,
    "fullscreen": true,
    "volume": true,
    "quality": true
  },
  "skin": {
    "name": "minimal"
  },
  "share": {
    "embed": true,
    "link": true,
    "facebook": true,
    "twitter": true,
    "share_type": "PLAYER"
  },
  "recommendations": {
    "advance": false,
    "interval": 0,
    "source":"dynamic"
  },
  "restrictions": ["flowplayer.com", "apple.com"],
  "language": {
    "name": "ENG"
  },
  "default_quality": "MEDIUM",
  "preload": "METADATA",
  "version": "FLOWPLAYER_7",
  "loop": false
}
```

### HTTP Request

`PUT https://app.flowplayer.com/ovp/workspaces/:workspace_id/player-config`


### Request parameters

Parameter | Description
--------- | -------------------------------------
name      | The player name
ad_schedule | `optional` The platform ad schedule connected to this player. The player will use this ad schedules configuration to request ads.
responsive | `optional`  If the player by default should be presented as responsive. Default value is `true`.
height | `optional`  In case the player is not set as `responsive` this property is used to set the height of the player in pixels. Default value is `360`.
width | `optional`  In case the player is not set as `responsive` this property is used to set the width of the player in pixels. Default value is `640`.
logo[] | `optional`  An array containing all logos that should be rendered on the player
logo[].src | Url to the logo image
logo[].position | Position in the player for the logo. Possible values are `left` or `right` and depending on the value the logo will be places in either the upper left or upper right corner.
autoplay | `optional`  If the player should auto start. Default value is `false`.
muted | `optional`  If the player should start muted. Default value is `false`.
loop | `optional`  If the player should loop the content. Default value is `false`.
cast | `optional`  If the player should have `Chromecast` and `Airplay` support. Default value is `true`.
skin | `optional`  Contains the name of the skin in use. Different values depending on the player's version
appearance | `optional`  Content of appearance depends on the version of the player.
appearance.brand_color | Supported in both `Native` and  `7`. Sets the colour of for example the progress bar.
appearance.controls | Supported in both `Native` and  `7`. If controls should be visible in player.
appearance.show_title | Supported in both `Native` and  `7`. If the media asset title should be visible in player.
appearance.show_description | Supported in both `Native` and  `7`. If the media asset description should be visible in player.
appearance.fullscreen | Supported in both `Native` and  `7`. If fullscreen button and functionality is available in player.
appearance.volume | Supported in both `Native` and  `7`. If volume button is available in player.
appearance.playback_rate | Supported in both `Native` and  `7`. If playback rate button is available in player.
appearance.quality | Supported in both `Native` and  `7`. If quality selection button is available in player.
appearance.outlined | Supported in `7`. If `outlined` style is used in player.
appearance.rounded | Supported in `7`. If `rounded` style is used in player.
share | `optional`  Contains the configuration of the Social Sharing plugin
share.embed | Supported in both `Native` and  `7`. If embed options is available in Share screen.
share.link | Supported in both `Native` and  `7`. If link options is available in Share screen.
share.facebook | Supported in both `Native` and  `7`. If facebook options is available in Share screen.
share.twitter | Supported in both `Native` and  `7`. If twitter options is available in Share screen.
share.share_type | Supported in both `Native` and  `7`. Determines what should be shared in the different options. Possible values `PLAYER` or `PARENT`, where `PARENT` will share the page where the player is embedded and `PLAYER` will share the Iframe if player is embedded with Platform Iframe-embed.
recommendations | `optional`  Settings for how to rendered recommendations.
recommendations.advance | If `true` it will automatically start playing the next video. Default value is `false`.
recommendations.interval | Determines the wait time until next video automatically will start playing. Default value is `0`.
recommendations.source | Determines with type of content to be display in the recommendations screen. We have three different possible value `none`, `playlist` and `dynamic`. No recommendations will be displayed if `none` is set. With `dynamic` the platform will automatically fill the recommendation screen with videos related to the displayed video. For `playlist` it will use the playlist specified in `recommendation_playlist` to fetch videos. By default `dynamic` will be used.
recommendation_playlist | `optional`  The playlist, if any, that will be used to fetch videos to the recommendations screen.
restrictions | `optional`  An array containing host where the player is allowed to render.
language.name | `optional`  Language used in the player. Possible values: TODO.  Default value is `ENG`.
default_quality | `optional`   Starting quality used to fetch the first segments of HLS streams. Possible values `LOW`, `MEDIUM`, `HIGH`. Default value is `MEDIUM`.
preload | `optional`  Preloading setting that determines how the player should handle video data loading before play. Possible values `NONE`, `METADATA`, `AUTO`. Default value is `METADATA`.
version | `optional`  Player version used by this player. Possible values `VIDEO_JS`, `FLOWPLAYER_7`, `NATIVE`. Default value is taken from Workspace default player version.
release_channel | `optional`  To use either `EDGE` or  `STABLE` version of `Native` player. This property is only supported by `Native` version. Default value is `STABLE`.


## Update Player

Endpoint for updating a Player

> Endpoint for updating a Player

```shell
curl "https://app.flowplayer.com/ovp/workspaces/:workspace_id/player-config/:player_id"
```

```json
{
  "name": "Demo Trial Default",
  "responsive": true,
  "height": 360,
  "width": 640,
  "autoplay": false,
  "muted": false,
  "cast": true,
  "appearance": {
    "outlined": true,
    "rounded": true,
    "show_description": true,
    "show_title": true,
    "brand_color": "ffff22",
    "controls": true,
    "fullscreen": true,
    "volume": true,
    "quality": true
  },
  "skin": {
    "name": "minimal"
  },
  "share": {
    "embed": true,
    "link": true,
    "facebook": true,
    "twitter": true,
    "share_type": "PLAYER"
  },
  "recommendations": {
    "advance": false,
    "interval": 0,
    "source": "dynamic"
  },
  "restrictions": ["flowplayer.com", "apple.com"],
  "language": {
    "name": "ENG"
  },
  "default_quality": "MEDIUM",
  "preload": "METADATA",
  "version": "FLOWPLAYER_7",
  "loop": false
}
```

### HTTP Request

`PUT https://app.flowplayer.com/ovp/workspaces/:workspace_id/player-config/:player_id`


### Request parameters

Parameter | Description
--------- | -------------------------------------
name      | The player name
ad_schedule | `optional` The platform ad schedule connected to this player. The player will use this ad schedules configuration to request ads.
responsive | `optional`  If the player by default should be presented as responsive. Default value is `true`.
height | `optional`  In case the player is not set as `responsive` this property is used to set the height of the player in pixels. Default value is `360`.
width | `optional`  In case the player is not set as `responsive` this property is used to set the width of the player in pixels. Default value is `640`.
logo[] | `optional`  An array containing all logos that should be rendered on the player. Logo object do not support partial updates. All existing logo configurations will be removed on update. If you want to update the Player without changing anything in logo you should leave out the property in the update request.
logo[].src | Url to the logo image
logo[].position | Position in the player for the logo. Possible values are `left` or `right` and depending on the value the logo will be places in either the upper left or upper right corner.
autoplay | `optional`  If the player should auto start. Default value is `false`.
muted | `optional`  If the player should start muted. Default value is `false`.
loop | `optional`  If the player should loop the content. Default value is `false`.
cast | `optional`  If the player should have `Chromecast` and `Airplay` support. Default value is `true`.
skin | `optional`  Contains the name of the skin in use. Different values depending on the player's version
appearance | `optional`  Content of appearance depends on the version of the player. Appearance object do not support partial updates. All existing configurations in appearance will be removed on update. If you want to update the Player without changing anything in appearance you should leave out the property in the update request.
appearance.brand_color | Supported in both `Native` and  `7`. Sets the colour of for example the progress bar.
appearance.controls | Supported in both `Native` and  `7`. If controls should be visible in player.
appearance.show_title | Supported in both `Native` and  `7`. If the media asset title should be visible in player.
appearance.show_description | Supported in both `Native` and  `7`. If the media asset description should be visible in player.
appearance.fullscreen | Supported in both `Native` and  `7`. If fullscreen button and functionality is available in player.
appearance.volume | Supported in both `Native` and  `7`. If volume button is available in player.
appearance.playback_rate | Supported in both `Native` and  `7`. If playback rate button is available in player.
appearance.quality | Supported in both `Native` and  `7`. If quality selection button is available in player.
appearance.outlined | Supported in `7`. If `outlined` style is used in player.
appearance.rounded | Supported in `7`. If `rounded` style is used in player.
share | `optional`  Contains the configuration of the Social Sharing plugin. Share object do not support partial updates. All existing share configurations will be removed on update. If you want to update the Player without changing anything in share you should leave out the property in the update request.
share.embed | Supported in both `Native` and  `7`. If embed options is available in Share screen.
share.link | Supported in both `Native` and  `7`. If link options is available in Share screen.
share.facebook | Supported in both `Native` and  `7`. If facebook options is available in Share screen.
share.twitter | Supported in both `Native` and  `7`. If twitter options is available in Share screen.
share.share_type | Supported in both `Native` and  `7`. Determines what should be shared in the different options. Possible values `PLAYER` or `PARENT`, where `PARENT` will share the page where the player is embedded and `PLAYER` will share the Iframe if player is embedded with Platform Iframe-embed.
recommendations | `optional`  Settings for how to rendered recommendations. Recommendations object do not support partial updates. All existing recommendations configurations will be removed on update. If you want to update the Player without changing anything in recommendations you should leave out the property in the update request.
recommendations.advance | If `true` it will automatically start playing the next video. Default value is `false`.
recommendations.interval | Determines the wait time until next video automatically will start playing. Default value is `0`.
recommendations.source | Determines with type of content to be display in the recommendations screen. We have three different possible value `none`, `playlist` and `dynamic`. No recommendations will be displayed if `none` is set. With `dynamic` the platform will automatically fill the recommendation screen with videos related to the displayed video. For `playlist` it will use the playlist specified in `recommendation_playlist` to fetch videos. By default `dynamic` will be used.
recommendation_playlist | `optional`  The playlist, if any, that will be used to fetch videos to the recommendations screen.
restrictions | `optional`  An array containing host where the player is allowed to render. Restrictions array do not support partial updates. All existing restrictions configurations will be removed on update. If you want to update the Player without changing anything in restrictions you should leave out the property in the update request.
language.name | `optional`  Language used in the player. Possible values: TODO.  Default value is `ENG`.
default_quality | `optional`   Starting quality used to fetch the first segments of HLS streams. Possible values `LOW`, `MEDIUM`, `HIGH`. Default value is `MEDIUM`.
preload | `optional`  Preloading setting that determines how the player should handle video data loading before play. Possible values `NONE`, `METADATA`, `AUTO`. Default value is `METADATA`.
version | `optional`  Player version used by this player. Possible values `VIDEO_JS`, `FLOWPLAYER_7`, `NATIVE`. Default value is taken from Workspace default player version.
release_channel | `optional`  To use either `EDGE` or  `STABLE` version of `Native` player. This property is only supported by `Native` version. Default value is `STABLE`.

## Delete Player

Endpoint for deleting one single player

> Endpoint for deleting one single player


```shell
curl -X DELETE "https://app.flowplayer.com/ovp/workspaces/:player_id/player-config/:player_id"
```

```json
{
	"success":"ok"
}
```

### HTTP Request

`DELETE https://app.flowplayer.com/ovp/workspaces/:workspace_id/player-config/:player_id`

### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified Workspace or Player is not found
406         | If your either tries to delete a player that is the Workspace default player or the last remaining player on your Workspace.
