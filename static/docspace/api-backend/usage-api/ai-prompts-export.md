# aiPromptsExport

Referenced types are defined in the [full reference](../newai.md).

> AiPromptBundle aiPromptsExport()

`GET /api/2.0/ai/prompts/export`

Export the prompt library

Builds a versioned bundle of every prompt and folder in the caller&#39;s library and returns it, with no parameters. The bundle is self-contained: it carries its own format version so an older export can still be read back, and it is the input &#x60;POST api/2.0/ai/prompts/import-bundle&#x60; expects. This is also the only way to read the whole library at once, since listing is folder-scoped. Nothing is changed by the call.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The whole library as a versioned bundle, ready to import. | [**AiPromptBundle**](../newai.md#model-aipromptbundle) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiPromptBundle**](../newai.md#model-aipromptbundle)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
