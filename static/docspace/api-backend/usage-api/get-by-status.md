# getByStatus

Referenced types are defined in the [full reference](../people.md).

> EmployeeFullArrayWrapper getByStatus(status, filterBy, count, startIndex, sortBy, sortOrder, filterSeparator, filterValue)

`GET /api/2.0/people/status/{status}`

Get profiles by status

Returns a list of profiles filtered by the user status.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **status** | path | **EmployeeStatus** | The user status. | [required] [example: 1] [enum: 1, 2, 4, 5, 7] |
| **filterBy** | query | **String** | Specifies the criteria used to filter the profiles in the request. | [optional] [example: displayName] |
| **count** | query | **Integer** (int32) | The maximum number of user profiles to retrieve. | [optional] [example: 25] [min: 1] [max: 100] |
| **startIndex** | query | **Integer** (int32) | The starting index for retrieving data in a paginated request. | [optional] [example: 0] |
| **sortBy** | query | **String** | Specifies the property or field name by which the results should be sorted. | [optional] [example: displayName] |
| **sortOrder** | query | **SortOrder** | The order in which the results are sorted. | [optional] [example: 0] [enum: 0, 1] |
| **filterSeparator** | query | **String** | Represents the separator used to split multiple filter criteria in a query string. | [optional] [example: ,] |
| **filterValue** | query | **String** | A string value representing additional filter criteria used in query parameters. | [optional] [example: John] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | List of users with the detailed information | [**EmployeeFullArrayWrapper**](../people.md#model-employeefullarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
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
