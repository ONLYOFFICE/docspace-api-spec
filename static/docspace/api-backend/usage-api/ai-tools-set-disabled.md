# aiToolsSetDisabled

Referenced types are defined in the [full reference](../newai.md).

> AiSuccessResponse aiToolsSetDisabled(aiToolsSetDisabled\_request)

`PUT /api/2.0/ai/tools/set-disabled`

Set disabled

Marks the listed tools of one server type as switched off, so the model is no longer offered them.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiToolsSetDisabled\_request** | body | [**aiToolsSetDisabled_request**](../newai.md#model-aitoolssetdisabled-request-body) |  | [required] |

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
