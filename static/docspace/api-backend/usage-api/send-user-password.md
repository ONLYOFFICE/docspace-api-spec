# sendUserPassword

Referenced types are defined in the [full reference](../people.md).

> StringWrapper sendUserPassword(EmailMemberRequestDto)

`POST /api/2.0/people/password`

Remind a user password

Sends a password recovery email to the specified user address.  For unauthenticated requests, CAPTCHA validation is required when CAPTCHA is enabled in the configuration.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **EmailMemberRequestDto** | body | [**EmailMemberRequestDto**](../people.md#model-emailmemberrequestdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Email with the password | [**StringWrapper**](../people.md#model-stringwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | No permissions to perform this action | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**StringWrapper**](../people.md#model-stringwrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## PeoplePhotosApi
