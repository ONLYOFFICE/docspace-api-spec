# aiAgentsResetQuota

Referenced types are defined in the [full reference](../newai.md).

> AiFolderIntegerArrayWrapper aiAgentsResetQuota(aiAgentsResetQuota\_request)

`PUT /api/2.0/ai/agents/resetquota`

Reset agents&#39; quota

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiAgentsResetQuota\_request** | body | [**aiAgentsResetQuota_request**](../newai.md#model-aiagentsresetquota-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiFolderIntegerArrayWrapper**](../newai.md#model-aifolderintegerarraywrapper) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiFolderIntegerArrayWrapper**](../newai.md#model-aifolderintegerarraywrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
