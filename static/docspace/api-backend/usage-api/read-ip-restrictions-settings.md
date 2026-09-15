# readIpRestrictionsSettings

Referenced types are defined in the [full reference](../api.md).

> IPRestrictionsSettingsWrapper readIpRestrictionsSettings()

`GET /api/2.0/settings/iprestrictions/settings`

Get IP restriction settings

Reports whether the IP restrictions of the current portal are enforced, as the &#x60;enable&#x60; flag together with the  &#x60;lastModified&#x60; stamp of the setting. The caller needs the portal-settings right of a DocSpace administrator,  otherwise the call is refused. The call is read-only and honours &#x60;If-Modified-Since&#x60;: send back the  &#x60;Last-Modified&#x60; value of an earlier answer and an unchanged setting comes back as an empty not-modified  response rather than a body. The flag is &#x60;false&#x60; on a portal nobody has configured. A &#x60;true&#x60; flag on its own  blocks nothing: enforcement also needs at least one stored address, which this answer does not carry - read  the addresses with &#x60;GET api/2.0/settings/iprestrictions&#x60; - and it is skipped entirely on an installation whose  configuration hides the IP security section. Even when enforced, the portal owner and the installation&#39;s own  networks are let through. Change the flag with &#x60;PUT api/2.0/settings/iprestrictions/settings&#x60;, which replaces  the address list in the same call, so resend the addresses in force when all that changes is the flag.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The enforcement flag of the IP restrictions and the date the setting was last modified | [**IPRestrictionsSettingsWrapper**](../api.md#model-iprestrictionssettingswrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**IPRestrictionsSettingsWrapper**](../api.md#model-iprestrictionssettingswrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
