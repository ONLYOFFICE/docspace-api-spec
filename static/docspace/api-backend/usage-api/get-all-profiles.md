# getAllProfiles

Referenced types are defined in the [full reference](../people.md).

> EmployeeFullArrayWrapper getAllProfiles(count, startIndex, filterBy, sortBy, sortOrder, filterSeparator, filterValue)

`GET /api/2.0/people`

Get the active profiles

Returns a page of the working accounts of the portal, with the full profile of each of them.  It reports only the accounts whose status is &#x60;Active&#x60;, so disabled accounts and open invitations are never  listed - use &#x60;GET api/2.0/people/status/{status}&#x60; for those, or &#x60;GET api/2.0/people/filter&#x60; to search across  every state.  The caller has to be a room admin, a DocSpace admin or a People module admin; a member or a guest gets 403.  The call is read-only, paged by &#x60;count&#x60; and &#x60;startIndex&#x60;, ordered by &#x60;sortBy&#x60; and &#x60;sortOrder&#x60;, and reports  the number of matches in the total count of the response.  Narrow it with &#x60;filterValue&#x60; on the name and the email, and with &#x60;filterBy&#x60; set to &#x60;group&#x60; to keep only the  members of the group whose ID is passed in &#x60;filterValue&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **count** | query | **Integer** (int32) | The size of the page. It defaults to 100, which is also the largest value the operation accepts. | [optional] [example: 25] [min: 1] [max: 100] |
| **startIndex** | query | **Integer** (int32) | The number of matches to skip before the page starts. It defaults to 0, and the total number of matches is  reported in the total count of the response. | [optional] [example: 0] |
| **filterBy** | query | **String** | The only recognised value is &#x60;group&#x60;, which makes &#x60;filterValue&#x60; the ID of the group to keep the members of.  Any other value, and omitting the field, applies no group filter. | [optional] [example: group] |
| **sortBy** | query | **String** | What to order the accounts by, compared without regard to case: &#x60;FirstName&#x60;, &#x60;LastName&#x60;, &#x60;DisplayName&#x60;,  &#x60;Type&#x60;, &#x60;Email&#x60;, &#x60;Department&#x60;, &#x60;UsedSpace&#x60;, &#x60;CreatedBy&#x60; or &#x60;RegistrationDate&#x60;. | [optional] [example: DisplayName] |
| **sortOrder** | query | **SortOrder** | The direction of the ordering: &#x60;Ascending&#x60;, which is the default, or &#x60;Descending&#x60;. | [optional] [example: Ascending] [enum: 0, 1] |
| **filterSeparator** | query | **String** | The character that splits &#x60;filterValue&#x60; into several terms, of which any one may match. Omit it to split  the value on spaces instead, in which case every term has to match. | [optional] [example: ,] |
| **filterValue** | query | **String** | The text to match against the name and the email of the account, case-insensitively. Omit it to apply no  text filter. | [optional] [example: John] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | A page of active accounts, with their full profiles | [**EmployeeFullArrayWrapper**](../people.md#model-employeefullarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | The caller is a member or a guest | - | - |
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
