# getAllProfiles

Referenced types are defined in the [full reference](../people.md).

> EmployeeFullArrayWrapper getAllProfiles(count, startIndex, filterBy, sortBy, sortOrder, filterSeparator, filterValue)

`GET /api/2.0/people`

Get profiles

Returns a list of profiles for all the portal users.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **count** | query | **Integer** (int32) | The maximum number of items to be retrieved in the response. | [optional] [example: 25] [min: 1] [max: 100] |
| **startIndex** | query | **Integer** (int32) | The zero-based index of the first item to be retrieved in a filtered result set. | [optional] [example: 0] |
| **filterBy** | query | **String** | Specifies the filter criteria for user-related queries. | [optional] [example: displayName] |
| **sortBy** | query | **String** | Specifies the property or field name by which the results should be sorted. | [optional] [example: displayName] |
| **sortOrder** | query | **SortOrder** | The order in which the results are sorted. | [optional] [example: 0] [enum: 0, 1] |
| **filterSeparator** | query | **String** | The character or string used to separate multiple filter values in a filtering query. | [optional] [example: ,] |
| **filterValue** | query | **String** | The text value used as an additional filter criterion for profiles retrieval. | [optional] [example: John] |

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
