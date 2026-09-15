# getTenantQuota

Referenced types are defined in the [full reference](../api.md).

> DocsCloudQuotaWrapper getTenantQuota(refresh)

`GET /api/2.0/settings/docscloud/tenant/quota`

Get the DocsCloud tenant quota

Returns the DocsCloud user quota of the current portal: the users who currently count as DocsCloud editors and  the users who count as viewers, each with the identifier DocsCloud knows them by and the date their quota entry  expires. The portal must have an activated DocsCloud tenant, granted by &#x60;POST api/2.0/settings/docscloud/trial&#x60;  or by a DocsCloud purchase: an empty result from &#x60;GET api/2.0/settings/docscloud/tenant&#x60; means there is none  and this call fails with 400. The caller must be a portal administrator allowed to edit the portal settings,  on an installation where the DocsCloud service is configured. The call is read-only, idempotent and cached for  a minute, so pass &#x60;refresh&#x3D;true&#x60; to read the current state from DocsCloud. In the result, &#x60;users&#x60; holds the  editor entries and &#x60;usersView&#x60; the viewer entries, both unordered; &#x60;userId&#x60; is the DocSpace user ID for a  portal member and an identifier of DocsCloud&#39;s own for anyone else; &#x60;expire&#x60; is the date and time the entry  expires, as a UTC string; and empty lists mean no user has been counted yet. It lists the users themselves,  not the counters: the license limits with the per-role totals are in  &#x60;GET api/2.0/settings/docscloud/tenant/info&#x60;, a single active-user total is in &#x60;.../tenant/usage&#x60;, and the  same lists as a downloadable xlsx file are produced by  &#x60;POST api/2.0/settings/docscloud/tenant/quota/report&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **refresh** | query | **Boolean** | Pass &#x60;true&#x60; to skip the cached copy and request the user quota from DocsCloud again, replacing the cached one; with the default &#x60;false&#x60; the answer may be up to a minute old. | [optional] [default to false] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The editor and viewer users of the DocsCloud tenant of the portal, with the expiration date of each entry | [**DocsCloudQuotaWrapper**](../api.md#model-docscloudquotawrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The portal has no activated DocsCloud tenant, so there is no user quota to return | - | - |
| **403** | The caller is not allowed to edit the portal settings | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**DocsCloudQuotaWrapper**](../api.md#model-docscloudquotawrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
