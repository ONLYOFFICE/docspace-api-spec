# aiToolsRemoveCustomServer

Referenced types are defined in the [full reference](../newai.md).

> AiSuccessResponse aiToolsRemoveCustomServer(aiToolsRemoveCustomServer\_request)

`DELETE /api/2.0/ai/tools/remove-custom-server`

Remove custom server

Removes a custom MCP server from the registry.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiToolsRemoveCustomServer\_request** | body | [**aiToolsRemoveCustomServer_request**](../newai.md#model-aitoolsremovecustomserver-request-body) |  | [required] |

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
