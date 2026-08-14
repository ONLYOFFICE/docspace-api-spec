# getCspSettings

Referenced types are defined in the [full reference](../api.md).

> CspWrapper getCspSettings()

`GET /api/2.0/security/csp`

Get CSP settings

Returns the CSP (Content Security Policy) settings for the current portal.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Ok | [**CspWrapper**](../api.md#model-cspwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**CspWrapper**](../api.md#model-cspwrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

## SecurityFirebaseApi
