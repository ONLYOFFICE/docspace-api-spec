# aiThreadsCreate

Referenced types are defined in the [full reference](../newai.md).

> AiThread aiThreadsCreate(aiThreadsCreate\_request)

`POST /api/2.0/ai/threads/create`

Create

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiThreadsCreate\_request** | body | [**aiThreadsCreate_request**](../newai.md#model-aithreadscreate-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiThread**](../newai.md#model-aithread) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiThread**](../newai.md#model-aithread)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
