# getGroups

Referenced types are defined in the [full reference](../people.md).

> GroupArrayWrapper getGroups(userId, manager, count, startIndex, sortBy, sortOrder, filterValue)

`GET /api/2.0/group`

Get groups

Returns the groups of the portal, one page at a time, with the summary information about each of them - the  ID, the name and the manager - but without the member list.  The caller needs the permission to read groups.  The call is read-only, and the number of groups that match the filters is reported in the total count of the  response, so a client can page through them with &#x60;count&#x60; and &#x60;startIndex&#x60;.  Narrow the result with &#x60;filterValue&#x60; on the group name, with &#x60;userId&#x60; to keep only the groups that account  belongs to, and with &#x60;manager&#x60; set to true to keep only the groups it manages; order it with &#x60;sortBy&#x60; and  &#x60;sortOrder&#x60;, and an unknown &#x60;sortBy&#x60; falls back to sorting by title.  The entries carry no members - read &#x60;GET api/2.0/group/{id}&#x60; with &#x60;includeMembers&#x60; for one group, or  &#x60;GET api/2.0/group/user/{userid}&#x60; to find the groups of a single account.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **userId** | query | **UUID** (uuid) | Keeps only the groups the account with this ID takes part in. Omit it to search every group of the portal. | [optional] [example: 00000000-0000-0000-0000-000000000000] |
| **manager** | query | **Boolean** | Narrows &#x60;userId&#x60; down to the groups that account manages, instead of every group it belongs to. It has no  effect on its own and defaults to false. | [optional] [example: false] |
| **count** | query | **Integer** (int32) | The size of the page. It defaults to 100, which is also the largest value the operation accepts. | [optional] [example: 25] [min: 1] [max: 100] |
| **startIndex** | query | **Integer** (int32) | The number of matching groups to skip before the page starts. It defaults to 0, and the total number of  matches is reported in the total count of the response. | [optional] [example: 0] |
| **sortBy** | query | **String** | What to order the groups by: &#x60;Title&#x60;, &#x60;Manager&#x60; or &#x60;MembersCount&#x60;, compared without regard to case. Any other  value, and omitting the field, orders by title. | [optional] [example: Title] |
| **sortOrder** | query | **SortOrder** | The direction of the ordering: &#x60;Ascending&#x60;, which is the default, or &#x60;Descending&#x60;. | [optional] [example: Ascending] [enum: 0, 1] |
| **filterValue** | query | **String** | The text to match against the group name. Omit it to get every group. | [optional] [example: Marketing] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The matching groups, with their summary information | [**GroupArrayWrapper**](../people.md#model-grouparraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | No permissions to perform this action | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../people.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../people.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../people.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../people.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**GroupArrayWrapper**](../people.md#model-grouparraywrapper)

## Authorization

[Basic](../people.md#basic), [OAuth2](../people.md#oauth2) (scopes: read, write), [ApiKeyBearer](../people.md#apikeybearer), [asc_auth_key](../people.md#asc_auth_key), [Bearer](../people.md#bearer), [OpenId](../people.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
