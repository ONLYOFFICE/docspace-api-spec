# aiPromptsCreateFolder

Referenced types are defined in the [full reference](../newai.md).

> AiFolderMutationResult aiPromptsCreateFolder(body)

`POST /api/2.0/ai/prompts/create-folder`

Create folder

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **body** | body | **String** |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiFolderMutationResult**](../newai.md#model-aifoldermutationresult) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiFolderMutationResult**](../newai.md#model-aifoldermutationresult)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
