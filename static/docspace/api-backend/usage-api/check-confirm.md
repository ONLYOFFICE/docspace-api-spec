# checkConfirm

Referenced types are defined in the [full reference](../api.md).

> ConfirmWrapper checkConfirm(EmailValidationKeyModel)

`POST /api/2.0/authentication/confirm`

Open confirmation email URL

Opens a confirmation email URL to validate a certain action (employee invitation, portal removal, phone activation, etc.).

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **EmailValidationKeyModel** | body | [**EmailValidationKeyModel**](../api.md#model-emailvalidationkeymodel) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Validation result: Ok, Invalid, or Expired | [**ConfirmWrapper**](../api.md#model-confirmwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**ConfirmWrapper**](../api.md#model-confirmwrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
