# continuePortal

Referenced types are defined in the [full reference](../api.md).

> continuePortal()

`PUT /api/2.0/portal/continue`

Restore a portal

Brings a deactivated portal back to the active state, so its users can sign in again and its domain serves the  portal as before. It is reached only with the reactivation link that &#x60;POST api/2.0/portal/suspend&#x60; mails to  the portal owner: that link authorizes the call in place of an authentication token, and no ordinary token is  accepted here. The call is mutating and idempotent - it sets the status to active, re-applies the portal&#39;s  Content Security Policy and refreshes its base domain, and a portal that is already active is simply left  active. Nothing is returned in the body; read the result from &#x60;status&#x60; in &#x60;GET api/2.0/portal&#x60;. Deactivating  the portal again means asking for a fresh letter with &#x60;POST api/2.0/portal/suspend&#x60;, because each link is  issued for one operation. This operation cannot bring back a removed portal: the deletion behind  &#x60;DELETE api/2.0/portal/delete&#x60; is final, and a removed portal has to be restored from a backup instead.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | OK | - | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

null (empty response body)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
