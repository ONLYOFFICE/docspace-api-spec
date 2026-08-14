# searchUsersByExtendedFilter

Referenced types are defined in the [full reference](../people.md).

> EmployeeFullArrayWrapper searchUsersByExtendedFilter(employeeStatus, groupId, activationStatus, employeeType, employeeTypes, isAdministrator, payments, accountLoginType, quotaFilter, withoutGroup, excludeGroup, invitedByMe, inviterId, area, count, startIndex, sortBy, sortOrder, filterSeparator, filterValue)

`GET /api/2.0/people/filter`

Search users with detailed information by extended filter

Returns a list of users with full information about them matching the parameters specified in the request.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **employeeStatus** | query | **EmployeeStatus** | The user status. | [optional] [example: 1] [enum: 1, 2, 4, 5, 7] |
| **groupId** | query | **UUID** (uuid) | The group ID. | [optional] [example: 00000000-0000-0000-0000-000000000000] |
| **activationStatus** | query | **EmployeeActivationStatus** | The user activation status. | [optional] [example: 1] [enum: 0, 1, 2, 4] |
| **employeeType** | query | **EmployeeType** | The user type. | [optional] [example: 1] [enum: All, RoomAdmin, Guest, DocSpaceAdmin, User] |
| **employeeTypes** | query | **List** | The list of user types. | [optional] [example: [1,2]] [enum: 0, 1, 2, 3, 4] |
| **isAdministrator** | query | **Boolean** | Specifies if the user is an administrator or not. | [optional] [example: false] |
| **payments** | query | **Payments** | The user payment status. | [optional] [example: 0] [enum: 0, 1] |
| **accountLoginType** | query | **AccountLoginType** | The account login type. | [optional] [example: 0] [enum: 0, 1, 2] |
| **quotaFilter** | query | **QuotaFilter** | The quota filter (All - 0, Default - 1, Custom - 2). | [optional] [example: 0] [enum: 0, 1, 2] |
| **withoutGroup** | query | **Boolean** | Specifies whether the user should be a member of a group or not. | [optional] [example: false] |
| **excludeGroup** | query | **Boolean** | Specifies whether the user should be a member of the group with the specified ID. | [optional] [example: false] |
| **invitedByMe** | query | **Boolean** | Specifies whether the user is invited by the current user or not. | [optional] [example: false] |
| **inviterId** | query | **UUID** (uuid) | The inviter ID. | [optional] [example: 00000000-0000-0000-0000-000000000000] |
| **area** | query | **Area** | The filter area. | [optional] [example: 0] [enum: 0, 1, 2] |
| **count** | query | **Integer** (int32) | The maximum number of items to be retrieved in the response. | [optional] [example: 25] [min: 1] [max: 100] |
| **startIndex** | query | **Integer** (int32) | The zero-based index of the first item to be retrieved in a filtered result set. | [optional] [example: 0] |
| **sortBy** | query | **String** | Specifies the property or field name by which the results should be sorted. | [optional] [example: displayName] |
| **sortOrder** | query | **SortOrder** | The order in which the results are sorted. | [optional] [example: 0] [enum: 0, 1] |
| **filterSeparator** | query | **String** | Represents the separator used to split filter criteria in query parameters. | [optional] [example: ,] |
| **filterValue** | query | **String** | The search text used to filter results based on user input. | [optional] [example: John] |

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
