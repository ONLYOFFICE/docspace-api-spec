# aiToolsSetAllowAlways

Referenced types are defined in the [full reference](../newai.md).

> AiSuccessResponse aiToolsSetAllowAlways(aiToolsSetAllowAlways\_request)

`PUT /api/2.0/ai/tools/set-allow-always`

Set allow always

Adds a tool to the always-allow list, or removes it - the tools on that list run without an approval dialog.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiToolsSetAllowAlways\_request** | body | [**aiToolsSetAllowAlways_request**](../newai.md#model-aitoolssetallowalways-request-body) |  | [required] |

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
