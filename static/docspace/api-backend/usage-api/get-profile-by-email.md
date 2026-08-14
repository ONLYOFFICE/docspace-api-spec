# getProfileByEmail

Referenced types are defined in the [full reference](../people.md).

> EmployeeFullWrapper getProfileByEmail(email, encemail, culture)

`GET /api/2.0/people/email`

Get a profile by user email

Returns the detailed information about a profile of the user with the email specified in the request.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **email** | query | **String** (email) | The user email address. | [optional] [example: john.doe@example.com] [minLength: 0] [maxLength: 255] |
| **encemail** | query | **String** | The user encrypted email address. | [optional] [example: encrypted_email_string] |
| **culture** | query | **String** | Culture | [optional] [example: en-US] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Detailed profile information | [**EmployeeFullWrapper**](../people.md#model-employeefullwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | Incorrect email | - | - |
| **403** | No permissions to perform this action | - | - |
| **404** | User not found | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**EmployeeFullWrapper**](../people.md#model-employeefullwrapper)

## Authorization

[Basic](../people.md#basic), [OAuth2](../people.md#oauth2) (scopes: read, write), [ApiKeyBearer](../people.md#apikeybearer) (scopes: read, write), [asc_auth_key](../people.md#asc_auth_key) (scopes: read, write), [Bearer](../people.md#bearer), [OpenId](../people.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
