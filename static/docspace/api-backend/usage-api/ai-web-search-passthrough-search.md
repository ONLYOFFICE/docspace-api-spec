# aiWebSearchPassthroughSearch

Referenced types are defined in the [full reference](../newai.md).

> AiSuccessResponse aiWebSearchPassthroughSearch(request\_body)

`POST /api/2.0/ai/websearch/v1/search`

Web search proxied to the portal&#39;s active web-search provider

Runs a web search on behalf of the document editor&#39;s AI plugin. The plugin only holds a placeholder configuration; the portal&#39;s active provider and its key are resolved here and never reach the browser.

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
