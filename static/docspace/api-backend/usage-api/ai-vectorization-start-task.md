# aiVectorizationStartTask

Referenced types are defined in the [full reference](../newai.md).

> AiSuccessResponse aiVectorizationStartTask(request\_body)

`POST /api/2.0/ai/vectorization/tasks`

Start a vectorization task

Starts a vectorization task over the supplied portal files. The indexing itself runs asynchronously on the .NET side.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **request\_body** | body | **Map** |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiSuccessResponse**](../newai.md#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiSuccessResponse**](../newai.md#model-aisuccessresponse)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## AIWebSearchApi
