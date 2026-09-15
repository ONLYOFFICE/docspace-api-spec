# getWhiteLabelLogos

Referenced types are defined in the [full reference](../api.md).

> WhiteLabelItemArrayWrapper getWhiteLabelLogos(IsDark, IsDefault)

`GET /api/2.0/settings/whitelabel/logos`

Get the white label logos

Lists the branding logo slots of the current portal together with the image URLs to render, which is what a  login page, an editor or a mail template needs before any user is known. No authentication is required, and  the portal is resolved from the address the request is made to. The call is read-only and idempotent. Each  item carries the slot as a number in &#x60;type&#x60;, its stable name in &#x60;name&#x60;, the size the image is fitted to in  &#x60;size&#x60; (&#x60;width&#x60; and &#x60;height&#x60; in pixels), and the URLs in &#x60;path&#x60;. When &#x60;isDark&#x60; is passed, only the matching  theme is filled in, &#x60;light&#x60; for &#x60;false&#x60; and &#x60;dark&#x60; for &#x60;true&#x60;; when it is omitted both are filled in and  &#x60;dark&#x60; comes back empty for the slots that have no separate dark image. The notification slot is not part of  this list, as it is derived from the login-page logo and used only in letters. Pass &#x60;isDefault&#x3D;true&#x60; to read  the installation-wide default logos instead of this portal&#39;s. To learn which slots are still untouched use  &#x60;GET api/2.0/settings/whitelabel/logos/isdefault&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **IsDark** | query | **Boolean** | Which theme the answer is filled in for: &#x60;true&#x60; fills the dark image only, &#x60;false&#x60; the light one only.  Omitting it fills both, leaving the dark one empty for the slots that have no separate dark image. | [optional] [example: true] |
| **IsDefault** | query | **Boolean** | Whether the installation-wide default branding is addressed instead of this portal own. Writing the default  branding is only allowed on a self-hosted installation; elsewhere it is refused with 403. | [optional] [example: true] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The logo slots of the portal, each with its target size and the URLs of the light and dark images | [**WhiteLabelItemArrayWrapper**](../api.md#model-whitelabelitemarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**WhiteLabelItemArrayWrapper**](../api.md#model-whitelabelitemarraywrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
