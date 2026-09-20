# changeRoomCover

Referenced types are defined in the [full reference](../files.md).

> FolderWrapper changeRoomCover(id, CoverRequestDto)

`POST /api/2.0/files/rooms/{id}/cover`

Change the room cover

Sets the cover picture and the background colour a room is shown with, and returns the whole room afterwards.  &#x60;cover&#x60; accepts only an identifier listed by &#x60;GET api/2.0/files/rooms/covers&#x60;, and &#x60;color&#x60; only six  hexadecimal digits with no leading number sign, so anything else is rejected as an invalid request. Either  field may be sent on its own, an empty &#x60;cover&#x60; clears the picture, an empty &#x60;color&#x60; restores the default one,  and an empty body leaves the room untouched. The cover is what the room shows while it has no uploaded logo:  setting a logo with &#x60;POST api/2.0/files/rooms/{id}/logo&#x60; hides the cover without erasing it, and deleting that  logo brings it back. The caller must be a manager of the room, an archived room is refused with 403, and an  unknown or deleted room is answered with 404. Repeating the same request is harmless, and the cover survives  archiving and unarchiving.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | path | **Integer** (int32) | The room to change, named by the identifier that &#x60;GET api/2.0/files/rooms&#x60; reports for it. | [required] [example: 1] |
| **CoverRequestDto** | body | [**CoverRequestDto**](../files.md#model-coverrequestdto) | The cover and the colour to apply. Either half may be sent on its own, and an empty object leaves the room as  it is. | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The room as it is after the cover change | [**FolderWrapper**](../files.md#model-folderwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | The caller may not edit this room, or the room is archived | - | - |
| **404** | No room with this ID is visible to the caller | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../files.md#model-errorapiresponse) | - |
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
| **id** | path | **String** | The room to change, named by the identifier that &#x60;GET api/2.0/files/rooms&#x60; reports for it. | [required] [example: 1] |

Return type: [**ThirdPartyFolderWrapper**](../files.md#model-thirdpartyfolderwrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer), [asc_auth_key](../files.md#asc_auth_key), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
