# authenticateMeFromBodyWithCode

Referenced types are defined in the [full reference](../api.md).

> AuthenticationTokenWrapper authenticateMeFromBodyWithCode(code, AuthWithCodeRequestsDto)

`POST /api/2.0/authentication/{code}`

Authenticate a user by code

Authenticates the current user by SMS or two-factor authentication code.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **code** | path | **String** |  | [required] |
| **AuthWithCodeRequestsDto** | body | [**AuthWithCodeRequestsDto**](../api.md#model-authwithcoderequestsdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Authentication data | [**AuthenticationTokenWrapper**](../api.md#model-authenticationtokenwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | userName, password or passworHash is empty | - | - |
| **401** | User authentication failed | - | - |
| **403** | Auth code is not available | - | - |
| **429** | Too many login attempts. Please try again later | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**AuthenticationTokenWrapper**](../api.md#model-authenticationtokenwrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
