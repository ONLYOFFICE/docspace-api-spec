# getGroupsWithRoomsShared

Referenced types are defined in the [full reference](../people.md).

> GroupArrayWrapper getGroupsWithRoomsShared(id, excludeShared, count, startIndex, filterValue)

`GET /api/2.0/group/room/{id}`

Get groups with room sharing settings

Returns groups with their sharing settings in a room with the ID specified in request.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | path | **Integer** (int32) | The group ID. | [required] [example: 00000000-0000-0000-0000-000000000000] |
| **excludeShared** | query | **Boolean** | Specifies whether to exclude the group sharing settings from the response. | [optional] [example: false] |
| **count** | query | **Integer** (int32) | The number of groups to retrieve in the request. | [optional] [example: 25] [min: 1] [max: 100] |
| **startIndex** | query | **Integer** (int32) | The starting index from which to begin retrieving groups with their sharing settings. | [optional] [example: 0] |
| **filterValue** | query | **String** | The text used as a filter for retrieving groups with their sharing settings. | [optional] [example: John] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Ok | [**GroupArrayWrapper**](../people.md#model-grouparraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | No permissions to perform this action | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**GroupArrayWrapper**](../people.md#model-grouparraywrapper)

## Authorization

[Basic](../people.md#basic), [OAuth2](../people.md#oauth2) (scopes: read, write), [ApiKeyBearer](../people.md#apikeybearer) (scopes: read, write), [asc_auth_key](../people.md#asc_auth_key) (scopes: read, write), [Bearer](../people.md#bearer), [OpenId](../people.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

## PeopleEmailApi
