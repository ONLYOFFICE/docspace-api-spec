# aiWebSearchClear

Referenced types are defined in the [full reference](../newai.md).

> AiSuccessResponse aiWebSearchClear(body)

`DELETE /api/2.0/ai/web-search/clear`

Clear the web-search configuration

Removes the portal&#39;s web-search configuration, after which web search is unavailable everywhere it was not configured separately. This is not scoped: it takes no &#x60;entityId&#x60; and any body sent with it is ignored, so it cannot be used to clear one room&#39;s configuration. Clearing an already-unconfigured portal is not an error and the call answers success either way. The stored provider key is destroyed with the configuration and has to be entered again.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **body** | body | **String** | Ignored. The operation always clears the portal-wide configuration, so send an empty body; a value here does not scope it to a room. | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Confirms the portal has no web-search configuration any more. | [**AiSuccessResponse**](../newai.md#model-aisuccessresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiSuccessResponse**](../newai.md#model-aisuccessresponse)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
