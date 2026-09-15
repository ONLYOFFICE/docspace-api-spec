# getPortalInformation

Referenced types are defined in the [full reference](../api.md).

> TenantWrapper getPortalInformation()

`GET /api/2.0/portal`

Get portal information

Returns the portal the request was addressed to - the tenant behind the current domain - with its name, alias,  owner, language, time zone, industry, trusted-domain rules, version and creation date. Nothing has to be  called first, the call is read-only and idempotent, and it keeps answering while the portal&#39;s payment has  lapsed. What comes back depends on the caller&#39;s rights: a caller with the portal-settings right gets the whole  record, while every other user gets an object in which only &#x60;tenantId&#x60; is filled and no error is raised - so  check &#x60;tenantAlias&#x60; for null before reading the rest. &#x60;status&#x60; says whether the portal is active, suspended or  pending removal, and &#x60;creationDateTime&#x60;, &#x60;statusChangeDate&#x60;, &#x60;lastModified&#x60; and &#x60;versionChanged&#x60; are UTC.  &#x60;region&#x60; names the data-center region a hosted portal is served from and stays empty on a server installation  and when the portal cache is off, while &#x60;hostedRegion&#x60; is the region written on the record itself. The  settings of the same portal are read with &#x60;GET api/2.0/settings&#x60;, its tariff with &#x60;GET api/2.0/portal/tariff&#x60;  and its quota with &#x60;GET api/2.0/portal/quota&#x60;.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The portal record, or an object in which only &#x60;tenantId&#x60; is filled when the caller has no portal-settings right | [**TenantWrapper**](../api.md#model-tenantwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**TenantWrapper**](../api.md#model-tenantwrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
