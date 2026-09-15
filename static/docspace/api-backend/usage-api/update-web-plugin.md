# updateWebPlugin

Referenced types are defined in the [full reference](../api.md).

> updateWebPlugin(name, WebPluginRequests)

`PUT /api/2.0/settings/webplugins/{name}`

Update a web plugin

Switches a web plugin of the current portal on or off and stores the settings string the portal keeps for it.  The plugin has to be installed already, so upload its package with &#x60;POST api/2.0/settings/webplugins&#x60; first,  and &#x60;name&#x60; is its manifest name as published by &#x60;GET api/2.0/settings/webplugins&#x60;, matched without regard to  case. Editing the portal settings is required, so a portal owner or administrator, and the installation has to  have web plugins enabled in its configuration. The body replaces the stored state instead of merging into it,  which makes the call idempotent; &#x60;settings&#x60; is required, so send &#x60;{}&#x60; when there is nothing to keep, and it is  limited to 255 characters and stored encrypted for this portal alone. Switching the plugin on adds the domains  its manifest declares to the portal Content Security Policy and switching it off takes them away again, and  the connected clients are notified of the new state. Nothing is returned on success. A name that is not  installed is rejected as not found, and 403 means web plugins are switched off or the caller may not edit the  portal settings.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **name** | path | **String** | The plugin to change, by the manifest name &#x60;GET api/2.0/settings/webplugins&#x60; publishes as &#x60;name&#x60;, matched  without regard to case. It is neither the localized display name nor the JavaScript object name in  &#x60;pluginName&#x60;, so it cannot be read off the interface; a name that is not installed answers 404. | [required] [example: example-plugin] |
| **WebPluginRequests** | body | [**WebPluginRequests**](../api.md#model-webpluginrequests) | The whole state the plugin is to have afterwards. It replaces what was stored instead of merging into it, so  both the enabled flag and the settings have to be sent every time. | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The state and the settings of the web plugin are saved for the portal | - | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | Web plugins are switched off for the installation, or the caller may not edit the portal settings | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

null (empty response body)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## ThirdPartyApi
