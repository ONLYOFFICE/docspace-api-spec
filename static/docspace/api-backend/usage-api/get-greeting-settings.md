# getGreetingSettings

Referenced types are defined in the [full reference](../api.md).

> StringWrapper getGreetingSettings()

`GET /api/2.0/settings/greetingsettings`

Get greeting settings

Returns the greeting title of the current portal - the caption shown as the welcome heading on the sign-in  page, kept as the portal name. Any authenticated user may call it and no administrative right is needed; the  call is read-only. The title comes back as a bare string and is never empty: when the portal has no title of  its own, the built-in default caption is returned instead, localized to the caller&#39;s language. Because of that  fallback this operation cannot tell a saved title from the default one - call  &#x60;GET api/2.0/settings/greetingsettings/isdefault&#x60; when that distinction matters. The same string is part of  the portal settings answer as the &#x60;greetingSettings&#x60; field of &#x60;GET api/2.0/settings&#x60;, so a client that already  reads the settings needs no separate call. The value is a caption only: it is neither the portal address nor  the white-label logo text of the header, which is returned by &#x60;GET api/2.0/settings/whitelabel/logotext&#x60;.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The greeting title of the portal, or the localized default caption when the portal has no title of its own | [**StringWrapper**](../api.md#model-stringwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**StringWrapper**](../api.md#model-stringwrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
