# getPortalPath

Referenced types are defined in the [full reference](../api.md).

> StringWrapper getPortalPath(virtualPath)

`GET /api/2.0/portal/path`

Get a path to the portal

Turns a portal-relative path into the absolute URL a client can open, filling in the scheme, the current  portal domain and the virtual root the portal is hosted on. Any signed-in user may call it, nothing has to be  called first, and the call is read-only and idempotent - it neither checks that the path exists nor that the  caller is allowed to open it. &#x60;virtualPath&#x60; is taken as it is: an omitted or empty value yields the portal  root, a value starting with &#x60;/&#x60; is appended to that root, a value starting with &#x60;~/&#x60; is resolved against the  virtual root, and a value that already starts with &#x60;http://&#x60;, &#x60;https://&#x60; or &#x60;mailto:&#x60; is handed back  unchanged. The answer is a bare JSON string. The domain in the result is the one the portal answers on right  now, so a renamed portal starts returning the new domain without any change on the client. Use it to build  links that have to survive a rename; the portal&#39;s own addresses and settings are read from  &#x60;GET api/2.0/settings&#x60; instead.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **virtualPath** | query | **String** | The path to resolve. It is taken as it is: an omitted or empty value yields the portal root, a value starting  with &#x60;/&#x60; is appended to that root, a value starting with &#x60;~/&#x60; is resolved against the virtual root, and one  that already begins with &#x60;http://&#x60;, &#x60;https://&#x60; or &#x60;mailto:&#x60; is handed back unchanged. Nothing checks that the  path exists or that the caller may open it. | [optional] [example: /portal/documents] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The absolute URL that the given portal-relative path resolves to | [**StringWrapper**](../api.md#model-stringwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**StringWrapper**](../api.md#model-stringwrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
