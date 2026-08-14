# aiWebSearchConfigure

Referenced types are defined in the [full reference](../newai.md).

> AiWebSearchMutationResult aiWebSearchConfigure(aiWebSearchConfigure\_request)

`PUT /api/2.0/ai/web-search/configure`

Configure

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiWebSearchConfigure\_request** | body | [**aiWebSearchConfigure_request**](../newai.md#model-aiwebsearchconfigure-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiWebSearchMutationResult**](../newai.md#model-aiwebsearchmutationresult) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiWebSearchMutationResult**](../newai.md#model-aiwebsearchmutationresult)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
