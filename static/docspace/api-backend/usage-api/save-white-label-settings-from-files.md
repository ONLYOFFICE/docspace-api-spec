# saveWhiteLabelSettingsFromFiles

Referenced types are defined in the [full reference](../api.md).

> BooleanWrapper saveWhiteLabelSettingsFromFiles(IsDark, IsDefault)

`POST /api/2.0/settings/whitelabel/logos/savefromfiles`

Save the logos from files

Replaces the branding images of the current portal with the files sent as &#x60;multipart/form-data&#x60;, which is the  way to upload image files directly instead of embedding them as base64 in  &#x60;POST api/2.0/settings/whitelabel/logos/save&#x60;. The form field names are not used: each file is routed by its  own name, which has to start with the numeric logo slot published by &#x60;GET api/2.0/settings/whitelabel/logos&#x60;  and end with the image extension, as in &#x60;2.png&#x60;; a name that also contains &#x60;dark&#x60;, as in &#x60;2.dark.png&#x60;, is  stored as the dark-theme image of that slot. Slots that get no file keep the image they have, and a dark file  is ignored for the favicon and the editor logos, which have no dark variant. A request that carries no file at  all is rejected. Requires a DocSpace administrator and a plan that includes branding, which  &#x60;GET api/2.0/settings/enablewhitelabel&#x60; reports; otherwise the call is refused as payment required. It answers  &#x60;true&#x60;, overwrites in place and is undone by &#x60;PUT api/2.0/settings/whitelabel/logos/restore&#x60;. With  &#x60;isDefault&#x3D;true&#x60; it writes the installation-wide default branding, which only a server installation allows.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **IsDark** | query | **Boolean** | Which theme the answer is filled in for: &#x60;true&#x60; fills the dark image only, &#x60;false&#x60; the light one only.  Omitting it fills both, leaving the dark one empty for the slots that have no separate dark image. | [optional] [example: true] |
| **IsDefault** | query | **Boolean** | Whether the installation-wide default branding is addressed instead of this portal own. Writing the default  branding is only allowed on a self-hosted installation; elsewhere it is refused with 403. | [optional] [example: true] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Always &#x60;true&#x60; once the uploaded files have been stored as the portal logos | [**BooleanWrapper**](../api.md#model-booleanwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | The caller is not a DocSpace administrator, or the installation does not allow default branding to be edited | - | - |
| **409** | The request carried no file to store as a logo | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**BooleanWrapper**](../api.md#model-booleanwrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

## SettingsSSOApi
