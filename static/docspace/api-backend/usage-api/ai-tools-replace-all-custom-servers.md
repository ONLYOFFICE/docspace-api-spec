# aiToolsReplaceAllCustomServers

Referenced types are defined in the [full reference](../newai.md).

> AiToolsBulkResult aiToolsReplaceAllCustomServers(aiToolsReplaceAllCustomServers\_request)

`PUT /api/2.0/ai/tools/replace-all-custom-servers`

Replace all custom servers

Replaces the whole custom MCP server registry of the scope with the supplied map.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiToolsReplaceAllCustomServers\_request** | body | [**aiToolsReplaceAllCustomServers_request**](../newai.md#model-aitoolsreplaceallcustomservers-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiToolsBulkResult**](../newai.md#model-aitoolsbulkresult) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiToolsBulkResult**](../newai.md#model-aitoolsbulkresult)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
