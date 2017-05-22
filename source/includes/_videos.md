# Videos

Video management APIs

## List videos

> List videos

```shell
curl https://api.flowplayer.org/videos \
       -H "Authorization: <token>"
```

```javascript
const client = require('flowplayer-client')('<token>');

let videos = await client.videos.list();
````

> Response JSON - list of video objects

```json
[{
  "state" : "FINISHED",
  "created_at" : "2017-04-28T08:37:53.000Z",
  "id" : 97705,
  "encodings" : [
     {
        "url" : null,
        "mime_type" : "video/mp4",
        "type" : "original"
     },
     {
        "url" : "https://cdn.dev.flowplayer.org/44026/97705.mp4",
        "mime_type" : "video/mp4",
        "type" : "vod"
     },
     {
        "type" : "hls",
        "url" : "https://cdn.dev.flowplayer.org/44026/97705.m3u8",
        "mime_type" : "application/x-mpegurl"
     }
  ],
  "images" : [
     {
        "url" : "https://drive.cdn.dev.flowplayer.org/44026/97705-thumb.jpg",
        "type" : "thumbnail"
     },
     {
        "type" : "snapshot",
        "url" : "https://drive.cdn.dev.flowplayer.org/44026/97705-snap.jpg"
     }
  ],
  "duration" : 8,
  "published" : false,
  "description" : null,
  "name" : "My video",
  "published_at" : null,
  "updated_at" : "2017-04-29T05:31:03.000Z"
}]
```

Endpoint to list all videos associated with your account.

### HTTP request

`GET https://api.flowplayer.org/videos`



