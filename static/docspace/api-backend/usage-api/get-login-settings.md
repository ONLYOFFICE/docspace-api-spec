# getLoginSettings

Referenced types are defined in the [full reference](../api.md).

> LoginSettingsWrapper getLoginSettings()

`GET /api/2.0/settings/security/loginsettings`

Get login settings

Returns the brute-force protection of the sign-in form for the current portal: how many failed attempts are  tolerated, how long the window they are counted in lasts, and how long an offender stays blocked. The caller  needs the portal-settings right of a DocSpace administrator; members without it are refused, and anonymous  callers are not admitted. The operation is read-only and honours &#x60;If-Modified-Since&#x60;: send back the  &#x60;Last-Modified&#x60; value of an earlier answer and unchanged settings come back as an empty not-modified response  rather than a body. &#x60;checkPeriod&#x60; and &#x60;blockTime&#x60; are counted in seconds. A portal nobody has configured  tolerates 5 failed attempts inside a window of 60 seconds and blocks for 60 seconds, and reports &#x60;isDefault&#x60;  true; the flag turns false as soon as any of the three values differs from that. The answer describes the  portal-wide policy only: it does not say which accounts or addresses are blocked at the moment, while a  lockout that has already happened is recorded in the login history and can be read with  &#x60;GET api/2.0/security/audit/login/filter&#x60;. Change the numbers with  &#x60;PUT api/2.0/settings/security/loginsettings&#x60;, or put them back with  &#x60;DELETE api/2.0/settings/security/loginsettings&#x60;.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The brute-force protection settings of the portal: the tolerated attempts, the counting window and the block in seconds, and whether they match the shipped defaults | [**LoginSettingsWrapper**](../api.md#model-loginsettingswrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**LoginSettingsWrapper**](../api.md#model-loginsettingswrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
