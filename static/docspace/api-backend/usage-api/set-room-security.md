# setRoomSecurity

Referenced types are defined in the [full reference](../files.md).

> RoomSecurityWrapper setRoomSecurity(id, RoomInvitationRequest)

`PUT /api/2.0/files/rooms/{id}/share`

Set the room access rights

Sets the access rights to the room with the ID specified in the request.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | path | **Integer** (int32) | The room ID. | [required] [example: 1] |
| **RoomInvitationRequest** | body | [**RoomInvitationRequest**](../files.md#model-roominvitationrequest) | The room invitation request. | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Room security information | [**RoomSecurityWrapper**](../files.md#model-roomsecuritywrapper) | - |
| **401** | Unauthorized | - | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**RoomSecurityWrapper**](../files.md#model-roomsecuritywrapper)

## Authorization

[Basic](../files.md#basic), [OAuth2](../files.md#oauth2) (scopes: read, write), [ApiKeyBearer](../files.md#apikeybearer) (scopes: read, write), [asc_auth_key](../files.md#asc_auth_key) (scopes: read, write), [Bearer](../files.md#bearer), [OpenId](../files.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
