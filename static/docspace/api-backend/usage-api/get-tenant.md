# getTenant

Referenced types are defined in the [full reference](../api.md).

> DocsCloudTenantWrapper getTenant(refresh)

`GET /api/2.0/settings/docscloud/tenant`

Get the DocsCloud tenant

Returns the DocsCloud tenant of the current portal: the DocsCloud server assigned to the portal, with its  address, the date the tenant subscription ends and the payment the tenant was created for. A tenant exists  only after a DocsCloud subscription has been granted, by &#x60;POST api/2.0/settings/docscloud/trial&#x60; or by a  DocsCloud purchase, and only on an installation where the DocsCloud service is configured. The caller must  be a portal administrator allowed to edit the portal settings. The call is read-only and idempotent, and it  is served from a cache that keeps the tenant for an hour and the absence of a tenant for a minute, so pass  &#x60;refresh&#x3D;true&#x60; right after a subscription change to read the current state from DocsCloud instead. In the  result, &#x60;address&#x60; is the absolute URL of the assigned server, &#x60;isActive&#x60; tells whether &#x60;endDate&#x60; is still in  the future, and the dates are in UTC. An empty result means the portal has no DocsCloud tenant yet, which is  the normal state before a subscription and not an error, so this is the operation to call to find out whether  DocsCloud is activated at all. The license and server details, the editing settings, the user quota and the  usage statistics are not part of it: they live in &#x60;GET api/2.0/settings/docscloud/tenant/info&#x60;,  &#x60;.../tenant/config&#x60;, &#x60;.../tenant/quota&#x60; and &#x60;.../tenant/usage&#x60;, each of which fails with 400 while the  portal has no activated tenant.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **refresh** | query | **Boolean** | Pass &#x60;true&#x60; to skip the cached copy and request the tenant from DocsCloud again, replacing the cached one; with the default &#x60;false&#x60; the answer may be up to an hour old, or up to a minute old while the portal has no tenant. | [optional] [default to false] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The DocsCloud tenant of the portal, or an empty result if no DocsCloud tenant is assigned to it | [**DocsCloudTenantWrapper**](../api.md#model-docscloudtenantwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | The caller is not allowed to edit the portal settings | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**DocsCloudTenantWrapper**](../api.md#model-docscloudtenantwrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
