# saveWhiteLabelLogoText

Referenced types are defined in the [full reference](../api.md).

> BooleanWrapper saveWhiteLabelLogoText(IsDark, IsDefault, WhiteLabelRequestsDto)

`POST /api/2.0/settings/whitelabel/logotext/save`

Save the white label logo text

Sets the wordmark that the portal prints next to or instead of a logo image, on the login page, in the editors  and in notification letters. Only &#x60;logoText&#x60; from the request body is used here, and it is limited to 40  characters; a longer value is rejected as an invalid request. Sending an empty or blank text, or exactly the  built-in &#x60;ONLYOFFICE&#x60;, clears the setting instead of storing it, which has the same effect as  &#x60;PUT api/2.0/settings/whitelabel/logotext/restore&#x60;. Requires a DocSpace administrator and a plan that includes  branding, which &#x60;GET api/2.0/settings/enablewhitelabel&#x60; reports; otherwise the call is refused as payment  required. The call is mutating and idempotent: the previous text is overwritten and &#x60;true&#x60; comes back. Logo  images are not touched - they are saved by &#x60;POST api/2.0/settings/whitelabel/logos/save&#x60; - and the text is not  rendered into them. Pass &#x60;isDefault&#x3D;true&#x60; to write the installation-wide default wordmark instead of this  portal&#39;s, which only a server installation allows. Read the stored value back with  &#x60;GET api/2.0/settings/whitelabel/logotext&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **IsDark** | query | **Boolean** | Which theme the answer is filled in for: &#x60;true&#x60; fills the dark image only, &#x60;false&#x60; the light one only.  Omitting it fills both, leaving the dark one empty for the slots that have no separate dark image. | [optional] [example: true] |
| **IsDefault** | query | **Boolean** | Whether the installation-wide default branding is addressed instead of this portal own. Writing the default  branding is only allowed on a self-hosted installation; elsewhere it is refused with 403. | [optional] [example: true] |
| **WhiteLabelRequestsDto** | body | [**WhiteLabelRequestsDto**](../api.md#model-whitelabelrequestsdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Always &#x60;true&#x60; once the logo text has been stored for the portal | [**BooleanWrapper**](../api.md#model-booleanwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
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
