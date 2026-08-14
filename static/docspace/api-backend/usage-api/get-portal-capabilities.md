# getPortalCapabilities

Referenced types are defined in the [full reference](../api.md).

> CapabilitiesWrapper getPortalCapabilities()

`GET /api/2.0/capabilities`

Get portal capabilities

Returns the information about portal capabilities.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Portal capabilities | [**CapabilitiesWrapper**](../api.md#model-capabilitieswrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**CapabilitiesWrapper**](../api.md#model-capabilitieswrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

## MigrationApi
