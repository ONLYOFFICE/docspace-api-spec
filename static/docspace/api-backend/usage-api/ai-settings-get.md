# aiSettingsGet

Referenced types are defined in the [full reference](../newai.md).

> AiAiSettingsWrapper aiSettingsGet()

`GET /api/2.0/ai/config`

Get AI settings

Reports the portal&#39;s combined AI configuration and readiness.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiAiSettingsWrapper**](../newai.md#model-aiaisettingswrapper) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiAiSettingsWrapper**](../newai.md#model-aiaisettingswrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
