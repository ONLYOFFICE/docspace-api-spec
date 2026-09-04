# aiWebSearchPassthroughContents

Referenced types are defined in the [full reference](../newai.md).

> AiSuccessResponse aiWebSearchPassthroughContents(request\_body)

`POST /api/2.0/ai/websearch/v1/contents`

Web page contents proxied to the portal&#39;s active web-search provider

Fetches web page contents on behalf of the document editor&#39;s AI plugin, against the portal&#39;s active web-search provider, the same way as the search passthrough.

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
