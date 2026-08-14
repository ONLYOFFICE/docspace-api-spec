# getSmtpOperationStatus

Referenced types are defined in the [full reference](../api.md).

> SmtpOperationStatusRequestsWrapper getSmtpOperationStatus()

`GET /api/2.0/smtpsettings/smtp/test/status`

Get the SMTP testing process status

Returns the status of the SMTP testing process.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | SMTP operation status | [**SmtpOperationStatusRequestsWrapper**](../api.md#model-smtpoperationstatusrequestswrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **402** | Your pricing plan does not support this option | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**SmtpOperationStatusRequestsWrapper**](../api.md#model-smtpoperationstatusrequestswrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer) (scopes: read, write), [asc_auth_key](../api.md#asc_auth_key) (scopes: read, write), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
