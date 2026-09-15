# getPortalTariff

Referenced types are defined in the [full reference](../api.md).

> TariffWrapper getPortalTariff(refresh)

`GET /api/2.0/portal/tariff`

Get the portal tariff

Returns the tariff this portal runs on: its state, the end of the current period and the quotas - the plan and  its add-ons - it is made of. Nothing has to be called first, the call is read-only and idempotent, and it  keeps answering while the portal&#39;s payment has lapsed, which is what a client needs in order to show a payment  warning. How much of it is filled depends on the caller: every user gets &#x60;state&#x60;, which is &#x60;Trial&#x60;, &#x60;Paid&#x60;,  &#x60;Delay&#x60; for the grace period after the due date, or &#x60;NotPaid&#x60;; a room or DocSpace administrator also gets  &#x60;dueDate&#x60; and &#x60;delayDueDate&#x60;; and a caller with the portal-settings right additionally gets &#x60;id&#x60;,  &#x60;customerId&#x60;, &#x60;licenseDate&#x60;, the &#x60;openSource&#x60;, &#x60;enterprise&#x60; and &#x60;developer&#x60; flags and &#x60;quotas&#x60;, each entry  naming the quota, its quantity, its own due date and the quota it switches to next period. Dates are in the  portal time zone. Pass &#x60;refresh&#x3D;true&#x60; to re-read the tariff from the billing system instead of the portal  cache - it is slower, so use it after a payment, not on every page. What the next period will cost is listed  by &#x60;GET api/2.0/portal/tariff/upcoming&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **refresh** | query | **Boolean** | Whether the tariff is re-read from the billing system instead of the portal cache. The remote read is slower,  so ask for it right after a payment and leave it off for ordinary page loads. | [optional] [example: true] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The tariff of this portal, filled as far as the rights of the caller allow | [**TariffWrapper**](../api.md#model-tariffwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**TariffWrapper**](../api.md#model-tariffwrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
