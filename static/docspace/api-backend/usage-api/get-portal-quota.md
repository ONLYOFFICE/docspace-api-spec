# getPortalQuota

Referenced types are defined in the [full reference](../api.md).

> TenantQuotaWrapper getPortalQuota()

`GET /api/2.0/portal/quota`

Get the portal quota

Returns the quota this portal runs on - the allowance its tariff grants: how many users and paid users it may  have, how many rooms, the largest total and single-file size, the price of the quota and the feature flags  that go with it. The caller needs the portal-settings right and gets 403 without it; the call is read-only and  idempotent. Sizes are in bytes, and &#x60;maxTotalSize&#x60; comes back as &#x60;0&#x60; when the calling account&#39;s own role is  user, rather than as the real allowance. This is what the portal is allowed, not what it consumes: the  consumption is reported by &#x60;GET api/2.0/portal/usedspace&#x60; in gigabytes and by &#x60;GET api/2.0/portal/userscount&#x60;.  The quotas the portal could move to are listed by &#x60;GET api/2.0/portal/payment/quotas&#x60;, and  &#x60;GET api/2.0/portal/quota/right&#x60; picks the smallest of them that would still fit. A free or trial quota  carries no price, and the billing state that goes with the quota - paid, in grace period or not paid - is read  from &#x60;GET api/2.0/portal/tariff&#x60;.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The allowance the current tariff grants this portal, with sizes in bytes | [**TenantQuotaWrapper**](../api.md#model-tenantquotawrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | The caller has no portal-settings right | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**TenantQuotaWrapper**](../api.md#model-tenantquotawrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
