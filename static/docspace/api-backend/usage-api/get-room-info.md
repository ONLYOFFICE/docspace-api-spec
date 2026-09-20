# getRoomInfo

Referenced types are defined in the [full reference](../files.md).

> FolderWrapper getRoomInfo(id)

`GET /api/2.0/files/rooms/{id}`

Get room information

Returns one room with its type, title, tags, logo, cover, colour, quota and virtual data room settings,  together with the access level the caller has in it. Reading the room is not a side-effect-free call: it  clears the caller new-item badges for that room, and &#x60;newForMe&#x60; comes back as 0, so read  &#x60;GET api/2.0/files/rooms/{id}/news&#x60; first when the new items matter. The caller needs read access to the room;  portal administrators can read a room they were never invited to, while a member without access is refused.  The operation also answers an anonymous caller, but only in the context of a valid external share link of that  room, and a plain anonymous request is rejected as unauthenticated. A room that never existed, was deleted, or  lives in a section the caller cannot see is answered as missing. Archived rooms are returned as well and are  recognised by their root section rather than by a separate flag. Use &#x60;GET api/2.0/files/rooms&#x60; to search and  page through rooms instead of guessing ids.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | path | **Integer** (int32) | The room to act on, named by the identifier that &#x60;GET api/2.0/files/rooms&#x60; reports for it. Rooms kept in the  portal itself use whole numbers, while a room backed by a connected third-party account uses the string form  of the same listing. | [required] [example: 1] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The room with its settings and the access level of the caller | [**FolderWrapper**](../files.md#model-folderwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**FolderWrapper**](../files.md#model-folderwrapper)

## Third-party storage

For a file or folder in a connected third-party storage the identifier is a string such as `sbox-42`, and the call differs in these parts only:

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | path | **String** | The room to act on, named by the identifier that &#x60;GET api/2.0/files/rooms&#x60; reports for it. Rooms kept in the  portal itself use whole numbers, while a room backed by a connected third-party account uses the string form  of the same listing. | [required] [example: 1] |

Return type: [**ThirdPartyFolderWrapper**](../files.md#model-thirdpartyfolderwrapper)

## Authorization

[cookieAuth](../files.md#cookieauth), [bearerAuth](../files.md#bearerauth)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
