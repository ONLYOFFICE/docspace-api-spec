# getGroups

Referenced types are defined in the [full reference](../people.md).

> GroupArrayWrapper getGroups(userId, manager, count, startIndex, sortBy, sortOrder, filterValue)

`GET /api/2.0/group`

Get groups

Returns the general information about all the groups, such as group ID and group manager.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **userId** | query | **UUID** (uuid) | The user ID. | [optional] [example: 00000000-0000-0000-0000-000000000000] |
| **manager** | query | **Boolean** | Specifies if the user is a manager or not. | [optional] [example: false] |
| **count** | query | **Integer** (int32) | The number of records to retrieve. | [optional] [example: 25] [min: 1] [max: 100] |
| **startIndex** | query | **Integer** (int32) | The starting index for paginated results. | [optional] [example: 0] |
| **sortBy** | query | **String** | Specifies the property used to sort the query results. | [optional] [example: displayName] |
| **sortOrder** | query | **SortOrder** | The order in which the results are sorted. | [optional] [example: 0] [enum: 0, 1] |
| **filterValue** | query | **String** | The text used for filtering or searching group data. | [optional] [example: John] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | List of groups | [**GroupArrayWrapper**](../people.md#model-grouparraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
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
