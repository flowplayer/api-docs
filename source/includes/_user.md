# User

## Get User (NOT IMPLEMENTED)

Endpoint for fetching infomation about one single User

> Endpoint for fetching infomation about one single User

```shell
curl "TBD"
```

```json
{
    TBD
}
```

### HTTP Request

`GET TBD`


### Request parameters

### Response

Parameter | Description
--------- | -------------------------------------

### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified Playlist is not found


## List Users 

Endpoint for fetching all users in a Sitegroup. This is available for all users with Admin access on that Sitegroup. This query support filtering on sites. 

> Endpoint for fetching users with matching `flowplayer` on sites with id `SITE_ID_1` or `SITE_ID_2`

```shell
curl 'https://app.flowplayer.com/ovp/sitegroups/<SITEGROUP_ID>/users?query={"sort":{"by":"email","order","asc"},"search":"flowplayer","filters":[{"key":"site","value":["SITE_ID_1","SITE_ID_2"]}]}'
```

```javascript
 'https://app.flowplayer.com/ovp/sitegroups/<SITEGROUP_ID>/users?query={"sort":{"by":"email","order","asc"},"search":"flowplayer","filters":[{"key":"site","value":["SITE_ID_1","SITE_ID_2"]}]}'
```

```json
{
   {
    "query": {
        "page": 0,
        "page_size": 20,
        "search": "flowplayer",
        "sort": {
            "by": "email",
            "order": "ASC"
        },
        "filters": [
            {
                "key": "site",
                "value": [
                    "SITE_ID_1",
                    "SITE_ID_2"
                ]
            }
        ]
    },
    "total_count": 1639,
    "total_count_in_search": 1,
    "page": 0,
    "page_size": 20,
    "total_pages": 1,
    "search_term": "flowplayer",
    "assets": [
        {
            "id": "USER_ID_1",
            "active_site_id": "SITE_ID_1",
            "username": "flowplayer",
            "forum_name": "flowplayer",
            "display_name": null,
            "email": "flowplayer.no",
            "api_key": "",
            "time_zone": "(GMT+01:00) Stockholm",
            "avatar_id": null,
            "facebook_id": null,
            "first_video_uploaded": true,
            "created_at": "2015-11-30T14:05:19+0100",
            "updated_at": "2018-08-24T09:14:37+0200",
            "last_activity": "2018-08-27T08:54:56+0200",
            "site_edit_access": true,
            "video_access": true,
            "ad_access": true,
            "live_access": true,
            "user_only_access": false,
            "sitegroup_access": true,
            "acl": {
                "ads": true,
                "live": true,
                "site_edit": true,
                "sitegroup": true,
                "user_only": false,
                "video": true
            },
            "default_ui": 0,
            "sitegroup": {
                "id": "SITEGROUP_ID",
                "name": "Flowplayer",
                "created_at": "2015-06-17T22:28:00+0200",
                "fp_legacy_user_id": null,
                "subscription": {
                    "id": null,
                    "period_starts_at": null,
                    "period_ends_at": null,
                    "product": "none",
                    "state": "no_subscription_attached",
                    "over_trial_encoding_limit": false,
                    "over_trial_streaming_limit": false,
                    "deactivated": false
                },
                "acl": {
                    "ads": true,
                    "live": true,
                    "video": true
                },
                "settings": {
                    "distributor": false,
                    "https": true
                }
            },
            "sites": null,
            "emailNotification": "NONE"
        }
    ]
}
```



### HTTP Request

`GET https://app.flowplayer.com/sitegroups/<SITEGROUP_ID>/users`


### Request parameters

Parameter | Description
--------- | -------------------------------------
page        | `optional` - Page for response, default value is `0`.
page_size        | `optional` - Page size for response, default value is `20`.
search | `optional` - Search term for filtering the response. Searches `name`.
sort.by | `optional` - Sorting column for the response, default value is `created_at`. Possible values: `created_at`, `email`, `last_logged_in`.
sort.order | `optional` - Sorting order for the response, default value is `desc`. Possible values `asc` and `desc`
filter | `optional` - Filters available are currently only `site`. The value that should be used is `site_id`

### Response

Parameter | Description
--------- | -------------------------------------
TBD

### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request

## Create User

Endpoint for creating a Account. This endpoint will create User, User, User, Player configuration and demo videos needed when setting up an new account.

> Endpoint for creating an account

```shell
curl "https://app.flowplayer.com/ovp/account/create"
```

```json
{
}
```

### HTTP Request

`POST https://app.flowplayer.com/ovp/account/create`


### Request parameters

Parameter | Description
--------- | -------------------------------------

### Response

Parameter | Description
--------- | -------------------------------------

## Update User (NOT IMPLEMENTED)

### HTTP Request



### Request parameters

Parameter | Description
--------- | -------------------------------------
TBD

### Response

Parameter | Description
--------- | -------------------------------------
TDB

## Delete User 

Endpoint for deleting one single User. This will in some cases (when enterprise) not delete the videos on the User. 

### HTTP Request

`DELETE https://app.flowplayer.com/ovp/accounts/delete/{User_id}`

### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified User is not found