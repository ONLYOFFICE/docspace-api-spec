# addRoomGroup

Referenced types are defined in the [full reference](../files.md).

> RoomGroupWrapper addRoomGroup(RoomGroupRequestDto)

`POST /api/2.0/files/group`

Add a new room group

Creates a new room group with the specified name, icon, and list of rooms.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **RoomGroupRequestDto** | body | [**RoomGroupRequestDto**](../files.md#model-roomgrouprequestdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | OK | [**RoomGroupWrapper**](../files.md#model-roomgroupwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**RoomGroupWrapper**](../files.md#model-roomgroupwrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer) (scopes: read, write), [asc_auth_key](../files.md#asc_auth_key) (scopes: read, write), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
