# getIsDefaultWhiteLabelLogoText

Referenced types are defined in the [full reference](../api.md).

> IsDefaultWhiteLabelLogosWrapper getIsDefaultWhiteLabelLogoText(IsDark, IsDefault)

`GET /api/2.0/settings/whitelabel/logotext/isdefault`

Check the default logo text

Reports whether the current portal still uses the built-in wordmark or one that was stored for it, which is  what an interface needs to decide whether a Restore action applies to the text. Requires a DocSpace  administrator. The call is read-only and idempotent. The answer has the same shape as one entry of  &#x60;GET api/2.0/settings/whitelabel/logos/isdefault&#x60;, with &#x60;name&#x60; fixed to &#x60;logotext&#x60; and &#x60;default&#x60; set to &#x60;true&#x60;  while no text has been stored and to &#x60;false&#x60; once one has. Because &#x60;GET api/2.0/settings/whitelabel/logotext&#x60;  falls back to &#x60;ONLYOFFICE&#x60; when nothing is stored, this operation is the only way to tell a portal that  deliberately kept the built-in wordmark from one that saved the very same text. Pass &#x60;isDefault&#x3D;true&#x60; to  inspect the installation-wide default branding instead of this portal&#39;s. The flag turns back to &#x60;true&#x60; after  &#x60;PUT api/2.0/settings/whitelabel/logotext/restore&#x60;, and to &#x60;false&#x60; after  &#x60;POST api/2.0/settings/whitelabel/logotext/save&#x60;. Saving the built-in wordmark itself counts as clearing the  setting, so the flag stays &#x60;true&#x60; in that case as well.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **IsDark** | query | **Boolean** | Which theme the answer is filled in for: &#x60;true&#x60; fills the dark image only, &#x60;false&#x60; the light one only.  Omitting it fills both, leaving the dark one empty for the slots that have no separate dark image. | [optional] [example: true] |
| **IsDefault** | query | **Boolean** | Whether the installation-wide default branding is addressed instead of this portal own. Writing the default  branding is only allowed on a self-hosted installation; elsewhere it is refused with 403. | [optional] [example: true] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | A single &#x60;logotext&#x60; entry telling whether the portal still uses the built-in wordmark | [**IsDefaultWhiteLabelLogosWrapper**](../api.md#model-isdefaultwhitelabellogoswrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**IsDefaultWhiteLabelLogosWrapper**](../api.md#model-isdefaultwhitelabellogoswrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
