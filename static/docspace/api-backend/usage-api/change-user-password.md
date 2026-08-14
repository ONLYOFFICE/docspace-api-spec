# changeUserPassword

Referenced types are defined in the [full reference](../people.md).

> EmployeeFullWrapper changeUserPassword(userid, ChangePasswordRequest)

`PUT /api/2.0/people/{userid}/password`

Change a user password

Sets a new password to the user with the ID specified in the request.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **userid** | path | **UUID** (uuid) | The user ID. | [required] [example: 00000000-0000-0000-0000-000000000000] |
| **ChangePasswordRequest** | body | [**ChangePasswordRequest**](../people.md#model-changepasswordrequest) | The request parameters for updating a user password. | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Detailed user information | [**EmployeeFullWrapper**](../people.md#model-employeefullwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | Incorrect userId or password | - | - |
| **403** | The link is invalid or no permissions to perform this action | - | - |
| **404** | The user could not be found | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**EmployeeFullWrapper**](../people.md#model-employeefullwrapper)

## Authorization

[Basic](../people.md#basic), [OAuth2](../people.md#oauth2) (scopes: read, write), [ApiKeyBearer](../people.md#apikeybearer) (scopes: read, write), [asc_auth_key](../people.md#asc_auth_key) (scopes: read, write), [Bearer](../people.md#bearer), [OpenId](../people.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
