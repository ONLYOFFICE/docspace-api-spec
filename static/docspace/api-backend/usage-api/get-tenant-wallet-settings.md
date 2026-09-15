# getTenantWalletSettings

Referenced types are defined in the [full reference](../api.md).

> TenantWalletSettingsResponseWrapper getTenantWalletSettings()

`GET /api/2.0/portal/payment/topupsettings`

Get the auto top-up settings

Returns the portal&#39;s automatic wallet top-up settings - whether it is on, the balance that triggers a  charge, the balance it is topped up to, and the currency both are expressed in. Any DocSpace  administrator may read them, and unlike the operation that changes them this one needs neither a  billing customer nor a configured billing service, so it answers on a portal that has never paid for  anything. It is read-only and changes nothing.  A portal that has never configured top-up gets the defaults rather than an empty result: &#x60;enabled&#x60; is  false, &#x60;currency&#x60; is null, and &#x60;minBalance&#x60; and &#x60;upToBalance&#x60; are 0. Those two zeros are outside the  ranges &#x60;POST api/2.0/portal/payment/topupsettings&#x60; accepts - 5 to 1000 and 6 to 5000 - so the answer  cannot be sent straight back to it; supply real values instead. &#x60;lastModified&#x60; is  &#x60;0001-01-01T00:00:00&#x60; until the settings are stored for the first time.  &#x60;lowBalanceThreshold&#x60; and &#x60;lowBalanceNotified&#x60; are maintained by the portal itself: they are reported  here, but ignored when the settings are written.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The automatic top-up settings of the portal, or their defaults when it has never configured them | [**TenantWalletSettingsResponseWrapper**](../api.md#model-tenantwalletsettingsresponsewrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | The caller is not a DocSpace administrator | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**TenantWalletSettingsResponseWrapper**](../api.md#model-tenantwalletsettingsresponsewrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
