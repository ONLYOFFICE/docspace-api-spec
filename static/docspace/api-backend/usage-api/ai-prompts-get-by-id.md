# aiPromptsGetById

Referenced types are defined in the [full reference](../newai.md).

> AiPrompt aiPromptsGetById(id)

`GET /api/2.0/ai/prompts/get-by-id`

Get by id

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | query | **String** |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiPrompt**](../newai.md#model-aiprompt) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiPrompt**](../newai.md#model-aiprompt)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
