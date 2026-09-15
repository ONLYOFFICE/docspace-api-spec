# aiPromptsCreateFolder

Referenced types are defined in the [full reference](../newai.md).

> AiFolderMutationResult aiPromptsCreateFolder(body)

`POST /api/2.0/ai/prompts/create-folder`

Create folder

Creates a folder in the caller&#39;s prompt library and returns it. The name has to be non-empty and unique across that library. Folders do not nest: there is one flat level, so a folder cannot be created inside another. The answer carries the folder ID to use as &#x60;folderId&#x60; when saving or moving prompts.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **body** | body | **String** | The name of the folder to create, as a bare JSON string. | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Whether the folder was created, with it in &#x60;folder&#x60;. | [**AiFolderMutationResult**](../newai.md#model-aifoldermutationresult) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiFolderMutationResult**](../newai.md#model-aifoldermutationresult)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
