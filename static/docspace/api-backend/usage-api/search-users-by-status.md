# searchUsersByStatus

Referenced types are defined in the [full reference](../people.md).

> EmployeeFullArrayWrapper searchUsersByStatus(status, query, filterBy, filterValue)

`GET /api/2.0/people/status/{status}/search`

Search users by status filter

Returns a list of users matching the status filter and search query.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **status** | path | **EmployeeStatus** | The user status. | [required] [example: 1] [enum: 1, 2, 4, 5, 7] |
| **query** | query | **String** | The advanced search query. | [optional] [example: John] |
| **filterBy** | query | **String** | Specifies the criteria used to filter search results in advanced queries. | [optional] [example: displayName] |
| **filterValue** | query | **String** | The value used to filter the search query. | [optional] [example: John] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | List of users with the detailed information | [**EmployeeFullArrayWrapper**](../people.md#model-employeefullarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | No permissions to perform this action | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**EmployeeFullArrayWrapper**](../people.md#model-employeefullarraywrapper)

## Authorization

[Basic](../people.md#basic), [OAuth2](../people.md#oauth2) (scopes: read, write), [ApiKeyBearer](../people.md#apikeybearer) (scopes: read, write), [asc_auth_key](../people.md#asc_auth_key) (scopes: read, write), [Bearer](../people.md#bearer), [OpenId](../people.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

## PeopleThemeApi
