# getUsersWithFoldersShared

Referenced types are defined in the [full reference](../people.md).

> EmployeeFullArrayWrapper getUsersWithFoldersShared(id, employeeStatus, activationStatus, excludeShared, includeShared, invitedByMe, inviterId, area, employeeTypes, count, startIndex, filterSeparator, filterValue)

`GET /api/2.0/people/folder/{id}`

Get users with folder sharing settings

Returns the users with the sharing settings in a folder with the ID specified in request.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | path | **Integer** (int32) | The user ID. | [required] [example: 00000000-0000-0000-0000-000000000000] |
| **employeeStatus** | query | **EmployeeStatus** | The user status. | [optional] [example: 1] [enum: 1, 2, 4, 5, 7] |
| **activationStatus** | query | **EmployeeActivationStatus** | The user activation status. | [optional] [example: 1] [enum: 0, 1, 2, 4] |
| **excludeShared** | query | **Boolean** | Specifies whether to exclude the user sharing settings or not. | [optional] [example: false] |
| **includeShared** | query | **Boolean** | Specifies whether to include the user sharing settings or not. | [optional] [example: false] |
| **invitedByMe** | query | **Boolean** | Specifies whether the user was invited by the current user or not. | [optional] [example: false] |
| **inviterId** | query | **UUID** (uuid) | The inviter ID. | [optional] [example: 00000000-0000-0000-0000-000000000000] |
| **area** | query | **Area** | The user area. | [optional] [example: 0] [enum: 0, 1, 2] |
| **employeeTypes** | query | [**List**](../people.md#model-employeetype) | The list of user types. | [optional] [example: [1, 2]] |
| **count** | query | **Integer** (int32) | The maximum number of users to be retrieved in the request. | [optional] [example: 25] [min: 1] [max: 100] |
| **startIndex** | query | **Integer** (int32) | The zero-based index of the first record to retrieve in a paged query. | [optional] [example: 0] |
| **filterSeparator** | query | **String** | The character or string used to separate multiple filter values in a filtering query. | [optional] [example: ,] |
| **filterValue** | query | **String** | The filter text value used for searching or filtering user results. | [optional] [example: John] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Ok | [**EmployeeFullArrayWrapper**](../people.md#model-employeefullarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | No permissions to perform this action | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../people.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../people.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../people.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../people.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**EmployeeFullArrayWrapper**](../people.md#model-employeefullarraywrapper)

## Authorization

[Basic](../people.md#basic), [OAuth2](../people.md#oauth2) (scopes: read, write), [ApiKeyBearer](../people.md#apikeybearer), [asc_auth_key](../people.md#asc_auth_key), [Bearer](../people.md#bearer), [OpenId](../people.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
