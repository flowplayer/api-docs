# User

## Get User

Endpoint for fetching infomation about one single User. More information about user access roles can be found in our [help-section](https://flowplayer.com/help/users/account/managing-users#user-roles-funcationlity-and...).

> Endpoint for fetch one User with id `<user_id>` 

```shell
curl -X GET "https://api.flowplayer.com/ovp/users/account?id=<user_id>"
```

```json
{
    "active_site_id": "<WORKSPACE_ID_A>",
    "created_at": "2016-01-12T07:57:48+0100",
    "display_name": "OVP Flowplayer.com",
    "email": "video_player @ flowplayer.com",
    "email_notification": "NONE",
    "first_video_uploaded": true,
    "forum_name": "video_platform @ flowplayer.com",
    "id": "<USER_ID_1>",
    "last_activity": "2018-08-26T14:50:41+0200",
    "time_zone": "(GMT+01:00) Stockholm",
    "updated_at": "2018-09-24T17:09:12+0200",
    "username": "video_platform @ flowplayer.com",
    "acl": {
        "ads": true,
        "live": true,
        "video": true,
        "workspace_admin": true,
        "organization_admin": false,
    },
    "sitegroup": {
        "id": "<ORGANIZATION_ID>",
        "name": "ORGANIZATION",
    },
    "sites": [
        {
            "id": "<WORKSPACE_ID_A>",
            "name": "Workspace A",
            ...
        },
        {
            "id": "<WORKSPACE_ID_B>",
            "name": "Workspace B",
            ...
        }
    ]
}
```

### HTTP Request

`GET https://api.flowplayer.com/ovp/users/account?id=<user_id>`


### Request parameters

Parameter | Description
--------- | -------------------------------------
id   | id for user that should be fetched

### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified User is not found

### Response properties

Parameter | Description
--------- | -------------------------------------
email   | email-address for this user. Needs to be unique in Flowplayer.
forum_name | a in Flowplayer unique name. Sometimes refered to as `username`
display_name | a non unique name, usually the full name of the user
acl.ads | if the user should be able to configure ads
acl.live | if the user should have access to livestreams
acl.video | if the user should have access to videos
acl.workspace_admin | if the user should have admin access to the workspaces it have access to
acl.organization_admin | if the user should access to everything on the organizations account
email_notification | should the user receive email notificiations on video uploads. Possible values `always` and `never`
time_zone |
avatar_id |
active_site_id | the id of the workspace that the users have as active
sites[] | Add and remove access to workspaces for a user by adding / removing workspaces in the sites-listing. This needs to include both `id` and `name` of the workspace.


## Update User

Endpoint for updating user information including `workspace`-access. More information about user access roles can be found in our [help-section](https://flowplayer.com/help/users/account/managing-users#user-roles-funcationlity-and...).

> Endpoint for update User with id `<user_id>` 

```shell
curl -X POST "https://api.flowplayer.com/ovp/users/<user_id>"
```

```json

"https://api.flowplayer.com/ovp/users/<user_id>"

{
    "active_site_id": "<WORKSPACE_ID_A>",
    "created_at": "2016-01-12T07:57:48+0100",
    "display_name": "OVP Flowplayer.com",
    "email": "video_player @ flowplayer.com",
    "email_notification": "NONE",
    "first_video_uploaded": true,
    "forum_name": "video_platform @ flowplayer.com",
    "id": "<USER_ID_1>",
    "last_activity": "2018-08-26T14:50:41+0200",
    "time_zone": "(GMT+01:00) Stockholm",
    "updated_at": "2018-09-24T17:09:12+0200",
    "username": "video_platform @ flowplayer.com",
    "acl": {
        "ads": true,
        "live": true,
        "video": true,
        "workspace_admin": true,
        "organization_admin": false,
    },
    "sitegroup": {
        "id": "<ORGANIZATION_ID>",
        "name": "ORGANIZATION",
    },
    "sites": [
        {
            "id": "<WORKSPACE_ID_A>",
            "name": "Workspace A",
            ...
        },
        {
            "id": "<WORKSPACE_ID_B>",
            "name": "Workspace B",
            ...
        }
    ]
}
```

### HTTP Request

`POST https://api.flowplayer.com/ovp/users/<user_id>`


### Request parameters

Parameter | Description
--------- | -------------------------------------
user_id   | id for user that should be updated

### Request body properties

Parameter | Description
--------- | -------------------------------------
email   | email-address for this user. Needs to be unique in Flowplayer.
forum_name | a in Flowplayer unique name. Sometimes refered to as `username`
display_name | a non unique name, usually the full name of the user
acl.ads | if the user should be able to configure ads
acl.live | if the user should have access to livestreams
acl.video | if the user should have access to videos
acl.workspace_admin | if the user should have admin access to the workspaces it have access to
acl.organization_admin | if the user should access to everything on the organizations account
email_notification | should the user receive email notificiations on video uploads. Possible values `always` and `never`
time_zone |
avatar_id |
active_site_id | the id of the workspace that the users have as active
sites[] | Add and remove access to workspaces for a user by adding / removing workspaces in the sites-listing. This needs to include both `id` and `name` of the workspace.

### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
422         | If the request is unproccessable due to bad formatted request body or illegal values ( for example an already used email-address )
404         | If the specified User is not found

## Delete User

Endpoint for deleting a User from the platform. After deletion this user will not be visible in listings or able to login on platform, but all videos and livestreams created by this users will still be available as before deletion. Videos and livestreams must be deleted separatly.

> Endpoint for deleting User with id `<user_id>` 

```shell
curl -X DELETE "https://api.flowplayer.com/ovp/users/<user_id>"
```

```json
{
    "success" : "ok"
}
```

### HTTP Request

`DELETE https://api.flowplayer.com/ovp/users/<user_id>`


### Request parameters

Parameter | Description
--------- | -------------------------------------
user_id   | id for user that should be deleted

### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified User is not found


## Add Workspace access for User

Endpoint for adding access for one User to a workspace in it's organization.

> Endpoint for adding access to Workspace with id `<workspace_id>` for User with id `<user_id>` 

```shell
curl -X PUT "https://api.flowplayer.com/ovp/users/<user_id>/site/<workspace_id>"
```

```json
{
    "success" : "ok"
}
```

### HTTP Request

`PUT https://api.flowplayer.com/ovp/users/<user_id>/site/<workspace_id>`


### Request parameters

Parameter | Description
--------- | -------------------------------------
user_id   | id for user that should have a new workspace added
workspace_id | id of workspace to be added


### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified Workspace or User is not found


## Remove Workspace access for User

Endpoint for removing access for one User to a workspace in it's organization.

> Endpoint for removing access to Workspace with id `<workspace_id>` for User with id `<user_id>` 

```shell
curl -X DELETE "https://api.flowplayer.com/ovp/users/<user_id>/site/<workspace_id>"
```

```json
{
    "success" : "ok"
}
```

### HTTP Request

`DELETE https://api.flowplayer.com/ovp/users/<user_id>/site/<workspace_id>`


### Request parameters

Parameter | Description
--------- | -------------------------------------
user_id   | id for user that should have a workspace removed
workspace_id | id of workspace to be removed


### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified Workspace or User is not found

## Resend Invite for User

Endpoint for resending invite to join the platform for a User.

> Endpoint for resending invite for User with id `<user_id>` 

```shell
curl "https://api.flowplayer.com/ovp/users/<user_id>/resend-invite?type=email"
```

```json
{
    "success" : "ok"
}
```

### HTTP Request

`GET https://api.flowplayer.com/ovp/users/<user_id>/resend-invite`


### Request parameters

Parameter | Description
--------- | -------------------------------------
user_id   | id for user that should receive a new invite
type | what type of invite to receive. Possible values are `google` (for users with Google Sign In) and `email`. If not specified it defaults to `email`.


### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified User is not found


## Revoke Invite for User

Endpoint for revoking invite to join the platform for a User.

> Endpoint for revoking invite for User with id `<user_id>` 

```shell
curl "https://api.flowplayer.com/ovp/users/<user_id>/revoke-invite"
```

```json
{
    "success" : "ok"
}
```

### HTTP Request

`GET https://api.flowplayer.com/ovp/users/<user_id>/revoke-invite`


### Request parameters

Parameter | Description
--------- | -------------------------------------
user_id   | id for user that should have all invites revoked


### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified User is not found

## List Users in Organization

Endpoint for fetching all users in a Organization. This is available for all users with Admin access on that Organization. This query support filtering on workspaces. 

> Endpoint for fetching users with matching `flowplayer` on workspaces with id `WORKSPACE_ID_1` or `WORKSPACE_ID_2`

```shell
curl 'https://app.flowplayer.com/ovp/organizations/<ORGANIZATION_ID>/users?query={"sort":{"by":"email","order","asc"},"search":"flowplayer","filters":[{"key":"workspace","value":["WORKSPACE_ID_1","WORKSPACE_ID_2"]}]}'
```

```javascript
 'https://app.flowplayer.com/ovp/organizations/<ORGANIZATION_ID>/users?query={"sort":{"by":"email","order","asc"},"search":"flowplayer","filters":[{"key":"workspace","value":["WORKSPACE_ID_1","WORKSPACE_ID_2"]}]}'
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
                "key": "workspace",
                "value": [
                    "WORKSPACE_ID_1",
                    "WORKSPACE_ID_2"
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
            "active_site_id": "WORKSPACE_ID_1",
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
                "id": "ORGANIZATION_ID",
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

`GET https://app.flowplayer.com/ovp/organizations/<ORGANIZATION_ID>/users`


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
