# getTenantUsage

Referenced types are defined in the [full reference](../api.md).

> DocsCloudUsageWrapper getTenantUsage(refresh)

`GET /api/2.0/settings/docscloud/tenant/usage`

Get the DocsCloud tenant usage

Returns the DocsCloud usage of the current portal: the number of users who have been active in DocsCloud in  the current period, and the moment that period is counted from. The portal must have an activated DocsCloud  tenant, granted by &#x60;POST api/2.0/settings/docscloud/trial&#x60; or by a DocsCloud purchase: an empty result from  &#x60;GET api/2.0/settings/docscloud/tenant&#x60; means there is none and this call fails with 400. The caller must be a  portal administrator allowed to edit the portal settings, on an installation where the DocsCloud service is  configured. The call is read-only, idempotent and cached for a minute, so pass &#x60;refresh&#x3D;true&#x60; to read the  current state from DocsCloud. In the result, &#x60;activeCount&#x60; counts the users seen since &#x60;since&#x60;, which is in  UTC, and it is one total for the whole tenant, with no split by role and no limit to compare it against. For  the editor and viewer breakdown with the license limits use &#x60;GET api/2.0/settings/docscloud/tenant/info&#x60;, and  for the users counted one by one &#x60;GET api/2.0/settings/docscloud/tenant/quota&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **refresh** | query | **Boolean** | Pass &#x60;true&#x60; to skip the cached copy and request the usage statistics from DocsCloud again, replacing the cached one; with the default &#x60;false&#x60; the answer may be up to a minute old. | [optional] [default to false] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The number of active DocsCloud users of the portal and the date the count starts from | [**DocsCloudUsageWrapper**](../api.md#model-docscloudusagewrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The portal has no activated DocsCloud tenant, so there is no usage information to return | - | - |
| **403** | The caller is not allowed to edit the portal settings | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**DocsCloudUsageWrapper**](../api.md#model-docscloudusagewrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
