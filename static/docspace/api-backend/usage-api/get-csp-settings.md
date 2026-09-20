# getCspSettings

Referenced types are defined in the [full reference](../api.md).

> CspWrapper getCspSettings()

`GET /api/2.0/security/csp`

Get CSP settings

Returns the Content Security Policy this portal serves: &#x60;domains&#x60;, the external hosts an administrator has  allowed, and &#x60;header&#x60;, the whole policy value built from them together with the portal&#39;s own defaults and the  integrations it has switched on. The operation is anonymous and reachable cross-origin - no token is needed -  because the login and editor front-ends read it before anyone has signed in. It is read-only for the caller,  but it does repair the portal&#39;s cached policy when the cache has lost it, so a call can rebuild the header  instead of only reading it. The answer honours &#x60;If-Modified-Since&#x60;: send back the &#x60;Last-Modified&#x60; value of an  earlier answer and an unchanged policy comes back as an empty not-modified response rather than a body.  &#x60;domains&#x60; is an empty list on a portal nobody has configured, while &#x60;header&#x60; is filled from the defaults even  then. Change the allowed domains with &#x60;POST api/2.0/security/csp&#x60;, which does need a DocSpace administrator.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The allowed domains and the full policy header the portal serves | [**CspWrapper**](../api.md#model-cspwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**CspWrapper**](../api.md#model-cspwrapper)

## Authorization

[cookieAuth](../api.md#cookieauth), [bearerAuth](../api.md#bearerauth)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

## SecurityFirebaseApi
