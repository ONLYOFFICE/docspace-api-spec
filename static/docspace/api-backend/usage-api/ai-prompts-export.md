# aiPromptsExport

Referenced types are defined in the [full reference](../newai.md).

> AiPromptBundle aiPromptsExport()

`GET /api/2.0/ai/prompts/export`

Export

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiPromptBundle**](../newai.md#model-aipromptbundle) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiPromptBundle**](../newai.md#model-aipromptbundle)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
