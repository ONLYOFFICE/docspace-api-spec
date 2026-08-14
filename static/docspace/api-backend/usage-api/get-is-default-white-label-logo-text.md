# getIsDefaultWhiteLabelLogoText

Referenced types are defined in the [full reference](../api.md).

> IsDefaultWhiteLabelLogosWrapper getIsDefaultWhiteLabelLogoText(IsDark, IsDefault)

`GET /api/2.0/settings/whitelabel/logotext/isdefault`

Check the default white label logo text

Specifies if the white label logo text is default or not.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **IsDark** | query | **Boolean** | Specifies if the white label logo is for the dark theme or not. | [optional] [example: true] |
| **IsDefault** | query | **Boolean** | Specifies if the logo is for a default tenant or not. | [optional] [example: true] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Request properties of white label logos | [**IsDefaultWhiteLabelLogosWrapper**](../api.md#model-isdefaultwhitelabellogoswrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**IsDefaultWhiteLabelLogosWrapper**](../api.md#model-isdefaultwhitelabellogoswrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer) (scopes: read, write), [asc_auth_key](../api.md#asc_auth_key) (scopes: read, write), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
