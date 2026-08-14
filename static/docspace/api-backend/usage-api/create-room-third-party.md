# createRoomThirdParty

Referenced types are defined in the [full reference](../files.md).

> FolderStringWrapper createRoomThirdParty(id, CreateThirdPartyRoom)

`POST /api/2.0/files/rooms/thirdparty/{id}`

Create a third-party room

Creates a room in the Rooms section stored in a third-party storage.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | path | **String** | The ID of the folder in the third-party storage in which the contents of the room will be stored. | [required] [example: folder-123-abc] |
| **CreateThirdPartyRoom** | body | [**CreateThirdPartyRoom**](../files.md#model-createthirdpartyroom) | The third-party room information. | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Room information | [**FolderStringWrapper**](../files.md#model-folderstringwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**FolderStringWrapper**](../files.md#model-folderstringwrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer) (scopes: read, write), [asc_auth_key](../files.md#asc_auth_key) (scopes: read, write), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
