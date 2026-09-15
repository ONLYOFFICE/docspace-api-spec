# aiAgentsResetQuota

Referenced types are defined in the [full reference](../newai.md).

> AiFolderIntegerArrayWrapper aiAgentsResetQuota(aiAgentsResetQuota\_request)

`PUT /api/2.0/ai/agents/resetquota`

Reset agents&#39; quota

Returns the listed AI agent rooms to the portal&#39;s default storage quota, forwarding &#x60;roomIds&#x60; to the DocSpace AI service unchanged. The answer is that service&#39;s payload, one updated room per entry. This is the counterpart of &#x60;PUT api/2.0/ai/agents/agentquota&#x60; and takes no quota value of its own. Rooms already on the default are unaffected.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiAgentsResetQuota\_request** | body | [**aiAgentsResetQuota_request**](../newai.md#model-aiagentsresetquota-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The updated agent rooms, one entry each. | [**AiFolderIntegerArrayWrapper**](../newai.md#model-aifolderintegerarraywrapper) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiFolderIntegerArrayWrapper**](../newai.md#model-aifolderintegerarraywrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
