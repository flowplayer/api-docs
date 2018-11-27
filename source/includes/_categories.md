# Category

## List categories

Endpoint for fetching infomation about categories on a specific Workspace. The response is list of categories.

> Endpoint for fetching infomation about categories on a specific Workspace.

```shell
curl "https://app.flowplayer.com/ovp/workspaces/:workspace_id/categories?query={"filters:[ {"key":"parent" , "value" : ["parent_id_1", "parent_id_2"]},{"key":"no_ads", "value" : true}],"search" :"flowplayer","sort" : { "by":"name","order":"asc"},"page":0, "page_size":20}"
```

```json
{
    "query": {
        "page": 0,
        "page_size": 20,
        "search": "",
        "sort": {
            "by": "name",
            "order": "ASC"
        },
        "filters": []
    },
    "total_count": 21,
    "total_count_in_search": 1,
    "page": 0,
    "page_size": 20,
    "total_pages": 1,
    "search_term": "flowplayer",
    "assets": [
        {
            "id": "f076a34e-6f54-4206-8d53-72a11c604b17",
            "name": "Flowplayer category",
            "no_ads":true,
            "ad_keywords":null
            
    ]
}
```



### HTTP Request

`GET https://app.flowplayer.com/ovp/workspaces/:workspace_id/categories`


### Request parameters

Parameter | Description
--------- | -------------------------------------
filters | It's possible to use multiple different filters in the query. The different filter keys are listed below.
key.parent | `optional` - The values should be an array of one or more category ids. The categories in the response will have one of the specified categories as their parent category.
key.no_ads | `optional` - To list only categories which `no_ads` set or not. Accepted values are `true` or `false`.
key.only_top_level | `optional` - If `true` only categories that are on top level, without parents, will be returned in the response.
page        | `optional` - Page for response, default value is `0`.
page_size        | `optional` - Page size for response, default value is `20`.
search | `optional` - Search term for filtering the response. Searches `name`, `description` and `tags`.
sort_by | `optional` - Sorting column for the response, default value is `name`. Possible values:  `name`.
sort_order | `optional` - Sorting order for the response, default value is `desc`. Possible values `asc` and `desc`

### Response

Parameter | Description
--------- | -------------------------------------
id        | The Category Id
name      | The Category name
no_ads    | If no ads should be displayed with livestreams or videos in this category
ad_keywords | A string that can be used to replaces macros in the players `ad tag url`.

### Errors

HTTP status | Description
----------- | --------------------------------------------
401         | If authorization fails for your request
404         | If the specified Workspace or livestream is not found

