# getThirdPartyCode

Referenced types are defined in the [full reference](../api.md).

> StringWrapper getThirdPartyCode(provider)

`GET /api/2.0/thirdparty/{provider}`

Get provider consent URL

Builds and returns, as a string, the OAuth 2.0 consent URL of one external provider - the address a client  opens in a browser so that the user can grant this portal access to their account. The provider&#39;s client id,  secret and redirect URI have to be saved for the portal first with &#x60;POST api/2.0/settings/authservice&#x60;;  without them the URL has no &#x60;client_id&#x60; and the provider refuses it. Any signed-in portal user may call it,  and the call is read-only and safe to repeat. The URL carries &#x60;response_type&#x3D;code&#x60;, the portal&#39;s &#x60;client_id&#x60;,  the provider&#39;s &#x60;redirect_uri&#x60;, the scope the portal needs (Drive with offline access for Google, &#x60;signature&#x60;  for DocuSign) and a &#x60;state&#x60; pointing back at this portal&#39;s &#x60;thirdparty/{provider}/code&#x60; page, where the code  arrives in the URL fragment as &#x60;#code&#x3D;...&#x60;, or &#x60;#error/...&#x60; when the user declines. Only Google &#x60;1&#x60;, Dropbox  &#x60;2&#x60;, Docusign &#x60;3&#x60;, Box &#x60;4&#x60;, OneDrive &#x60;5&#x60;, Wordpress &#x60;10&#x60; and Github &#x60;13&#x60; produce a URL; any other value is  answered with 200 and no URL instead of an error. With &#x60;desktop&#x3D;true&#x60;, the whole query string is copied into  &#x60;state&#x60; and comes back on the callback. The code is not exchanged here: pass it on as &#x60;token&#x60; to  &#x60;POST api/2.0/files/thirdparty&#x60; to connect the account.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **provider** | path | **LoginProvider** | The provider whose consent screen is wanted. Only Google, Dropbox, Docusign, Box, OneDrive, Wordpress and  Github produce a URL; any other provider is answered with 200 and no URL rather than an error. The provider  credentials have to be saved with &#x60;POST api/2.0/settings/authservice&#x60; first, or the URL comes back without a  client identifier and the provider refuses it. | [required] [enum: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The consent URL of the provider, ready to be opened in a browser; empty when the requested provider is not one of the seven this operation supports | [**StringWrapper**](../api.md#model-stringwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
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
