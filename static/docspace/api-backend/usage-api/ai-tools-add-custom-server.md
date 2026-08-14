# aiToolsAddCustomServer

Referenced types are defined in the [full reference](../newai.md).

> AiToolsMutationResult aiToolsAddCustomServer(aiToolsAddCustomServer\_request)

`POST /api/2.0/ai/tools/add-custom-server`

Add custom server

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiToolsAddCustomServer\_request** | body | [**aiToolsAddCustomServer_request**](../newai.md#model-aitoolsaddcustomserver-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiToolsMutationResult**](../newai.md#model-aitoolsmutationresult) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiToolsMutationResult**](../newai.md#model-aitoolsmutationresult)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
