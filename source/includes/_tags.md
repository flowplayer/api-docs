# Tags

## List Tags

List Tags on a Workspace

> List Livesources on a Workspace


```shell
curl "https://app.flowplayer.com/ovp/workspaces/:workspace_id/tags"
```

```json
{
    
https://adserver.adtech.de/?advideo/3.0/1779.1/6572111/0/0/cc=2;vidAS=pre_roll;vidRT=VAST;vidRTV=3.0;cors=yes;acao=https://imasdk.googleapis.com
https://adserver.adtech.de/?advideo/3.0/1779.1/6553192/0/0/cc=2;vidAS=pre_roll;vidRT=VAST;vidRTV=3.0;cors=yes;acao=https://imasdk.googleapis.com
}
```

### HTTP Request

`GET https://app.flowplayer.com/ovp/workspaces/:workspace_id/tags`

### Request parameters

Parameter | Description
--------- | -------------------------------------
page        | `optional` - Page for response, default value is `0`.
page_size        | `optional` - Page size for response, default value is `20`.
order | `optional` - To order tags. Default is `name` and possible values are `livecasts` and `videos` which will list the tag with most videos first if `videos` is been used.
filter | `optional` - Filter tags on popularity. The values describes how many videos or livecast that needs use the tags for being listed for each filter. Possible values: `popular`, `1_3`, `none`.
search | `optional` - Sorting column for the response, default value is `name`. Possible values: `name`.


### Response

Parameter | Description
--------- | -------------------------------------
active_filter | Filter that was used for creating response
page |
page_size |
total_pages |
total_tags | Total number of tags on this Site
total_tags_matching_search |
total_tags_matching_search_popular |
total_tags_matching_search_1_3 |
total_tags_matching_search_no |
tags[].id | Id for Tag
tags[].name | Tag 
tags[].videos | Number of videos using this tag
tags[].livecasts | Number of livecasts using this tag


### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified Site is not found


