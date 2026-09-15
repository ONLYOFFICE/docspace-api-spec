# saveWhiteLabelSettings

Referenced types are defined in the [full reference](../api.md).

> BooleanWrapper saveWhiteLabelSettings(IsDark, IsDefault, WhiteLabelRequestsDto)

`POST /api/2.0/settings/whitelabel/logos/save`

Save the white label logos

Replaces the branding images of the current portal with the ones sent in the request, so that the logos on the  login page, in the left menu, in the editors and in letters come from this portal. Every entry of &#x60;logo&#x60; names  a logo slot in its &#x60;key&#x60; - the numeric type published by &#x60;GET api/2.0/settings/whitelabel/logos&#x60; - and carries  the light-theme and the dark-theme image in &#x60;light&#x60; and &#x60;dark&#x60;. An image is either a  &#x60;data:image/png;base64,...&#x60; payload (&#x60;png&#x60;, &#x60;jpg&#x60; and &#x60;svg&#x60; are accepted) or the name of a file already  uploaded to the temporary store; a slot left out of the request keeps its image. The dark image is stored only  for the slots that have a dark variant, that is &#x60;1&#x60;, &#x60;2&#x60;, &#x60;6&#x60;, &#x60;7&#x60; and &#x60;8&#x60;, and is ignored for the favicon and  the editor logos; saving slot &#x60;2&#x60; also rebuilds the notification logo &#x60;8&#x60; from it. Requires a DocSpace  administrator and a plan that includes branding, which &#x60;GET api/2.0/settings/enablewhitelabel&#x60; reports;  otherwise the call is refused as payment required. It answers &#x60;true&#x60; and is undone by  &#x60;PUT api/2.0/settings/whitelabel/logos/restore&#x60;. With &#x60;isDefault&#x3D;true&#x60; it writes the installation-wide default  branding instead, which only a server installation allows. Uploaded files go to  &#x60;POST api/2.0/settings/whitelabel/logos/savefromfiles&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **IsDark** | query | **Boolean** | Which theme the answer is filled in for: &#x60;true&#x60; fills the dark image only, &#x60;false&#x60; the light one only.  Omitting it fills both, leaving the dark one empty for the slots that have no separate dark image. | [optional] [example: true] |
| **IsDefault** | query | **Boolean** | Whether the installation-wide default branding is addressed instead of this portal own. Writing the default  branding is only allowed on a self-hosted installation; elsewhere it is refused with 403. | [optional] [example: true] |
| **WhiteLabelRequestsDto** | body | [**WhiteLabelRequestsDto**](../api.md#model-whitelabelrequestsdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Always &#x60;true&#x60; once the submitted logos have been stored for the portal | [**BooleanWrapper**](../api.md#model-booleanwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | The caller is not a DocSpace administrator, or the installation does not allow default branding to be edited | - | - |
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

- **Content-Type**: application/json
- **Accept**: application/json
