# getWhiteLabelLogoText

Referenced types are defined in the [full reference](../api.md).

> StringWrapper getWhiteLabelLogoText(IsDark, IsDefault)

`GET /api/2.0/settings/whitelabel/logotext`

Get the white label logo text

Returns the wordmark the current portal prints next to or instead of a logo image, as a bare string rather  than an object. Requires a DocSpace administrator, because this is the settings view of the value; the  branding a login page needs is served by &#x60;GET api/2.0/settings/whitelabel/logos&#x60;, which needs no  authentication. The call is read-only and idempotent. When nothing has been stored for the portal, the  built-in &#x60;ONLYOFFICE&#x60; is returned, so the answer is never empty and cannot be used to tell a custom text from  the default one - &#x60;GET api/2.0/settings/whitelabel/logotext/isdefault&#x60; answers that question. Pass  &#x60;isDefault&#x3D;true&#x60; to read the installation-wide default wordmark instead of this portal&#39;s; without it the  portal&#39;s own value is returned even when the installation carries a different default. Change the text with  &#x60;POST api/2.0/settings/whitelabel/logotext/save&#x60; and clear it with  &#x60;PUT api/2.0/settings/whitelabel/logotext/restore&#x60;. The value is stored as it was typed, at most 40 characters  long, and is not translated for the caller&#39;s language, so the same wordmark is returned for every user of the  portal.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **IsDark** | query | **Boolean** | Which theme the answer is filled in for: &#x60;true&#x60; fills the dark image only, &#x60;false&#x60; the light one only.  Omitting it fills both, leaving the dark one empty for the slots that have no separate dark image. | [optional] [example: true] |
| **IsDefault** | query | **Boolean** | Whether the installation-wide default branding is addressed instead of this portal own. Writing the default  branding is only allowed on a self-hosted installation; elsewhere it is refused with 403. | [optional] [example: true] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The wordmark stored for the portal, or the built-in &#x60;ONLYOFFICE&#x60; when none is set | [**StringWrapper**](../api.md#model-stringwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
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
