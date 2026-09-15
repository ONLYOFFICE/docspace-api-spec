# getTenantConfig

Referenced types are defined in the [full reference](../api.md).

> DocsCloudConfigWrapper getTenantConfig(refresh)

`GET /api/2.0/settings/docscloud/tenant/config`

Get the DocsCloud tenant configuration

Returns the configuration of the DocsCloud tenant of the current portal: its name, the security secret and  header name, the file size limit and anonymous access switch of the server, the WOPI switch and the IP filter  rules. The portal must have an activated DocsCloud tenant, granted by &#x60;POST api/2.0/settings/docscloud/trial&#x60;  or by a DocsCloud purchase: an empty result from &#x60;GET api/2.0/settings/docscloud/tenant&#x60; means there is none  and this call fails with 400. The caller must be a portal administrator allowed to edit the portal settings,  on an installation where the DocsCloud service is configured. The call is read-only, idempotent and cached for  an hour, so pass &#x60;refresh&#x3D;true&#x60; to read the current state from DocsCloud; the same values are changed by  &#x60;PUT api/2.0/settings/docscloud/tenant/config&#x60;, which drops the cached copy itself, so no refresh is needed  after an update. In the result, &#x60;security.secret&#x60; is a credential, so the response should be treated as  sensitive; &#x60;server.fileSizeLimit&#x60; is in bytes and an update cannot raise it above 209715200 (200 MB); and an  empty or absent &#x60;ipFilter.rules&#x60; means no address restriction is configured. The license and server version,  the address of the assigned server, the per-user quota and the usage counters are not part of it: they live in  &#x60;.../tenant/info&#x60;, &#x60;.../tenant&#x60;, &#x60;.../tenant/quota&#x60; and &#x60;.../tenant/usage&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **refresh** | query | **Boolean** | Pass &#x60;true&#x60; to skip the cached copy and request the configuration from DocsCloud again, replacing the cached one; with the default &#x60;false&#x60; the answer may be up to an hour old. | [optional] [default to false] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The configuration of the DocsCloud tenant of the portal, with its security, server, WOPI and IP filter settings | [**DocsCloudConfigWrapper**](../api.md#model-docscloudconfigwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The portal has no activated DocsCloud tenant, so there is no configuration to return | - | - |
| **403** | The caller is not allowed to edit the portal settings | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**DocsCloudConfigWrapper**](../api.md#model-docscloudconfigwrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
