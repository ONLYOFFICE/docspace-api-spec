# aiThreadsRegenerateTitle

Referenced types are defined in the [full reference](../newai.md).

> String aiThreadsRegenerateTitle(aiThreadsRegenerateTitle\_request)

`POST /api/2.0/ai/threads/regenerate-title`

Regenerate title

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiThreadsRegenerateTitle\_request** | body | [**aiThreadsRegenerateTitle_request**](../newai.md#model-aithreadsregeneratetitle-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | **String** | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

**String**

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
