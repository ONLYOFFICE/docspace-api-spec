# getTenantInfo

Referenced types are defined in the [full reference](../api.md).

> DocsCloudTenantInfoWrapper getTenantInfo(refresh)

`GET /api/2.0/settings/docscloud/tenant/info`

Get the DocsCloud tenant information

Returns the DocsCloud license of the current portal, the DocsCloud server serving it, the user limits of  that license and the editor and viewer usage counted against them for the current period. The portal must  have an activated DocsCloud tenant, granted by &#x60;POST api/2.0/settings/docscloud/trial&#x60; or by a DocsCloud  purchase: an empty result from &#x60;GET api/2.0/settings/docscloud/tenant&#x60; means there is none and this call  fails with 400. The caller must be a portal administrator allowed to edit the portal settings, on an  installation where the DocsCloud service is configured. The call is read-only, idempotent and cached for a  minute, so pass &#x60;refresh&#x3D;true&#x60; right after a subscription change to read the current state from DocsCloud.  In the result, &#x60;license.valid&#x60; is when the license expires and &#x60;license.trial&#x60; is reported as &#x60;false&#x60; once  the portal holds a paid DocsCloud or DocsCloudDevPack subscription, even when the license itself still says  trial; &#x60;usersLimit&#x60; caps the editors and the viewers allowed, &#x60;stats&#x60; counts the active, internal, external  and remaining users of each of those two kinds over the last &#x60;stats.periodDay&#x60; days, and the dates are in  UTC. The editing settings, the per-user quota lists and the address of the assigned server live in  &#x60;.../tenant/config&#x60;, &#x60;.../tenant/quota&#x60; and &#x60;.../tenant&#x60;, while &#x60;.../tenant/usage&#x60; gives one active-user  total instead of this per-role breakdown.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **refresh** | query | **Boolean** | Pass &#x60;true&#x60; to skip the cached copy and request the license, server and usage information from DocsCloud again, replacing the cached one; with the default &#x60;false&#x60; the answer may be up to a minute old. | [optional] [default to false] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The DocsCloud license and server information of the portal, with the user limits of the license and the usage statistics for the current period | [**DocsCloudTenantInfoWrapper**](../api.md#model-docscloudtenantinfowrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The portal has no activated DocsCloud tenant, so there is no license information to return | - | - |
| **403** | The caller is not allowed to edit the portal settings | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**DocsCloudTenantInfoWrapper**](../api.md#model-docscloudtenantinfowrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
