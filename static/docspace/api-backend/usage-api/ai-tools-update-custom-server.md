# aiToolsUpdateCustomServer

Referenced types are defined in the [full reference](../newai.md).

> AiToolsMutationResult aiToolsUpdateCustomServer(aiToolsUpdateCustomServer\_request)

`PUT /api/2.0/ai/tools/update-custom-server`

Update custom server

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiToolsUpdateCustomServer\_request** | body | [**aiToolsUpdateCustomServer_request**](../newai.md#model-aitoolsupdatecustomserver-request-body) |  | [required] |

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

## AIVectorizationApi
