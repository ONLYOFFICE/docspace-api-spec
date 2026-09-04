# aiPromptsGetFolderById

Referenced types are defined in the [full reference](../newai.md).

> AiPromptFolder aiPromptsGetFolderById(id)

`GET /api/2.0/ai/prompts/get-folder-by-id`

Get folder by id

Returns one prompt folder, or an empty result when the identifier is unknown.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | query | **String** | The prompt folder identifier. | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiPromptFolder**](../newai.md#model-aipromptfolder) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiPromptFolder**](../newai.md#model-aipromptfolder)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
