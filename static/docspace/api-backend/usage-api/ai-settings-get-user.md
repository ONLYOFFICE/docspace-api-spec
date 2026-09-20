# aiSettingsGetUser

Referenced types are defined in the [full reference](../aichat.md).

> AiAiUserSettingsWrapper aiSettingsGetUser()

`GET /api/2.0/ai/config/user`

Get user AI settings

Returns the AI settings of the calling user, as opposed to the portal-wide ones. It takes no parameters - the user is the authenticated caller, and there is no way to read somebody else&#39;s settings - and is proxied unchanged to the DocSpace AI service. Use &#x60;GET api/2.0/ai/config&#x60; for the portal-wide configuration. This is a read-only operation.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The calling user&#39;s AI settings. | [**AiAiUserSettingsWrapper**](../aichat.md#model-aiaiusersettingswrapper) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |

## Return type

[**AiAiUserSettingsWrapper**](../aichat.md#model-aiaiusersettingswrapper)

## Authorization

[cookieAuth](../aichat.md#cookieauth), [bearerAuth](../aichat.md#bearerauth)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
