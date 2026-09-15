# getWebPlugin

Referenced types are defined in the [full reference](../api.md).

> WebPluginWrapper getWebPlugin(name)

`GET /api/2.0/settings/webplugins/{name}`

Get a web plugin by name

Returns one web plugin of the current portal by its manifest name, looked up over the same set as  &#x60;GET api/2.0/settings/webplugins&#x60;: the installation-wide plugins plus the portal&#39;s own. The &#x60;name&#x60; is the  manifest name published in the &#x60;name&#x60; field of that list, matched without regard to case; it is neither the  localized display name nor the JavaScript object name in &#x60;pluginName&#x60;, so it cannot be taken from the title  shown in the interface. Any authenticated portal member may call it, no settings permission needed, and the  installation has to have web plugins enabled in its configuration. The call is read-only and idempotent. The  response carries the manifest data along with the state the portal stored for that plugin: &#x60;enabled&#x60;, the  &#x60;settings&#x60; string, &#x60;system&#x60;, and the &#x60;url&#x60; and &#x60;cssUrl&#x60; a client loads it from. A name that is not installed  is rejected as not found, and 403 means web plugins are switched off for the installation. Change the state of  the plugin with &#x60;PUT api/2.0/settings/webplugins/{name}&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **name** | path | **String** | The plugin to act on, by the manifest name &#x60;GET api/2.0/settings/webplugins&#x60; publishes as &#x60;name&#x60;, matched  without regard to case. It is neither the localized display name nor the JavaScript object name in  &#x60;pluginName&#x60;; a name that is not installed answers 404. | [required] [example: example-plugin] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The requested web plugin with the state the portal stored for it | [**WebPluginWrapper**](../api.md#model-webpluginwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | Web plugins are switched off for the installation | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**WebPluginWrapper**](../api.md#model-webpluginwrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
