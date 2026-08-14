# signupThirdPartyAccount

Referenced types are defined in the [full reference](../people.md).

> EmployeeWrapper signupThirdPartyAccount(SignupAccountRequestDto)

`POST /api/2.0/people/thirdparty/signup`

Create a third-pary account

Creates a third-party account with the parameters specified in the request.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **SignupAccountRequestDto** | body | [**SignupAccountRequestDto**](../people.md#model-signupaccountrequestdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Ok | [**EmployeeWrapper**](../people.md#model-employeewrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | Incorrect email | - | - |
| **403** | The invitation link is invalid or its validity has expired | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**EmployeeWrapper**](../people.md#model-employeewrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
