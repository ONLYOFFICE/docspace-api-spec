# completeWizard

Referenced types are defined in the [full reference](../api.md).

> WizardSettingsWrapper completeWizard(WizardRequestsDto)

`PUT /api/2.0/settings/wizard/complete`

Complete the Wizard settings

Completes the Wizard settings.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **WizardRequestsDto** | body | [**WizardRequestsDto**](../api.md#model-wizardrequestsdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Wizard settings | [**WizardSettingsWrapper**](../api.md#model-wizardsettingswrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | Incorrect email address/The password is empty | - | - |
| **402** | You must enter a license key or license key is not correct or license expired or user quota does not match the license | - | - |
| **401** | Unauthorized | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**WizardSettingsWrapper**](../api.md#model-wizardsettingswrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer) (scopes: read, write), [asc_auth_key](../api.md#asc_auth_key) (scopes: read, write), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
