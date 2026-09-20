# aiSettingsSetUser

Referenced types are defined in the [full reference](../aichat.md).

> AiAiUserSettingsWrapper aiSettingsSetUser(request\_body)

`PUT /api/2.0/ai/config/user`

Update user AI settings

Replaces the AI settings of the calling user and returns the stored result. The body is proxied unchanged to the DocSpace AI service, which validates it, so a rejected value comes back with that service&#39;s verdict. Only the caller&#39;s own settings can be written. Portal-wide configuration is not touched by this operation.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **request\_body** | body | **Map** | The user&#39;s AI settings, proxied unchanged to the DocSpace AI service, which owns and validates the shape. Read the current one with &#x60;GET api/2.0/ai/config/user&#x60; and send it back changed. | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The calling user&#39;s stored AI settings. | [**AiAiUserSettingsWrapper**](../aichat.md#model-aiaiusersettingswrapper) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |

## Return type

[**AiAiUserSettingsWrapper**](../aichat.md#model-aiaiusersettingswrapper)

## Authorization

[cookieAuth](../aichat.md#cookieauth), [bearerAuth](../aichat.md#bearerauth)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
