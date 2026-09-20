# aiToolsSetDisabled

Referenced types are defined in the [full reference](../aichat.md).

> AiSuccessResponse aiToolsSetDisabled(aiToolsSetDisabled\_request)

`PUT /api/2.0/ai/tools/set-disabled`

Set disabled

Switches off the listed tools of one server type in the scope, so the model is no longer offered them. &#x60;serverType&#x60; has to be a key the round&#39;s tool filter actually matches - a host-configured system server, one of the two DocSpace integration groups, web search, image generation, or one of the scope&#39;s registered custom servers - and an unknown value is rejected with the list of valid ones in the message, rather than stored and silently ignored. &#x60;toolNames&#x60; replaces the previous selection for that server type, so send the full list and pass an empty one to switch everything back on. &#x60;entityId&#x60; has to name a room the caller can open.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiToolsSetDisabled\_request** | body | [**aiToolsSetDisabled_request**](../aichat.md#model-aitoolssetdisabled-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Confirms the new disable list was stored for that server type. | [**AiSuccessResponse**](../aichat.md#model-aisuccessresponse) | - |
| **400** | The list of tools to disable is malformed. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **404** | The referenced object does not exist, or the caller cannot access it - the two are deliberately indistinguishable, so a room the caller may not open answers 404 rather than 403. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |

## Return type

[**AiSuccessResponse**](../aichat.md#model-aisuccessresponse)

## Authorization

[cookieAuth](../aichat.md#cookieauth), [bearerAuth](../aichat.md#bearerauth)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
