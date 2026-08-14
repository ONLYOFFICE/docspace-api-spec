# getAccountsEntriesWithFoldersShared

Referenced types are defined in the [full reference](../people.md).

> ObjectArrayWrapper getAccountsEntriesWithFoldersShared(id, employeeStatus, activationStatus, excludeShared, includeShared, invitedByMe, inviterId, area, employeeTypes, count, startIndex, filterSeparator, filterValue)

`GET /api/2.0/accounts/folder/{id}/search`

Get account entries with folder sharing settings

Returns the account entries with their sharing settings in a folder with the ID specified in request.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | path | **Integer** (int32) | The user ID. | [required] [example: 00000000-0000-0000-0000-000000000000] |
| **employeeStatus** | query | **EmployeeStatus** | The user status. | [optional] [example: 1] [enum: 1, 2, 4, 5, 7] |
| **activationStatus** | query | **EmployeeActivationStatus** | The user activation status. | [optional] [example: 1] [enum: 0, 1, 2, 4] |
| **excludeShared** | query | **Boolean** | Specifies whether to exclude the account sharing settings from the response. | [optional] [example: false] |
| **includeShared** | query | **Boolean** | Specifies whether to include the account sharing settings in the response. | [optional] [example: false] |
| **invitedByMe** | query | **Boolean** | Specifies whether the user is invited by the current user or not. | [optional] [example: false] |
| **inviterId** | query | **UUID** (uuid) | The inviter ID. | [optional] [example: 00000000-0000-0000-0000-000000000000] |
| **area** | query | **Area** | The area of the account entries. | [optional] [example: 0] [enum: 0, 1, 2] |
| **employeeTypes** | query | [**List**](../people.md#model-employeetype) | The list of the user types. | [optional] [example: [1, 2]] |
| **count** | query | **Integer** (int32) | The number of items to retrieve in a request. | [optional] [example: 25] [min: 1] [max: 100] |
| **startIndex** | query | **Integer** (int32) | The starting index for the query results. | [optional] [example: 0] |
| **filterSeparator** | query | **String** | Specifies the separator used in filter expressions. | [optional] [example: ,] |
| **filterValue** | query | **String** | The text filter applied to the accounts search query. | [optional] [example: John] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Ok | [**ObjectArrayWrapper**](../people.md#model-objectarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | No permissions to perform this action | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**ObjectArrayWrapper**](../people.md#model-objectarraywrapper)

## Authorization

[Basic](../people.md#basic), [OAuth2](../people.md#oauth2) (scopes: read, write), [ApiKeyBearer](../people.md#apikeybearer) (scopes: read, write), [asc_auth_key](../people.md#asc_auth_key) (scopes: read, write), [Bearer](../people.md#bearer), [OpenId](../people.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
