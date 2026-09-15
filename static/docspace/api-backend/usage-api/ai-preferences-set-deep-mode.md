# aiPreferencesSetDeepMode

Referenced types are defined in the [full reference](../newai.md).

> AiSuccessResponse aiPreferencesSetDeepMode(aiPreferencesSetDeepMode\_request)

`PUT /api/2.0/ai/preferences/set-deep-mode`

Set deep mode

Stores the deep-mode toggle of a scope. &#x60;false&#x60; stores the &#x60;off&#x60; depth; &#x60;true&#x60; keeps the depth already stored and falls back to the default depth (&#x60;medium&#x60;) when none is. &#x60;value&#x60; has to be a real boolean: a string, a number or an absent value is rejected rather than coerced, so the string false cannot silently switch the setting on and an empty request cannot silently switch it off. &#x60;entityId&#x60; picks a room and omitting it writes the portal-wide preference. It is idempotent, so there is no need to read the current value first.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiPreferencesSetDeepMode\_request** | body | [**aiPreferencesSetDeepMode_request**](../newai.md#model-aipreferencessetdeepmode-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Confirms the preference was stored. | [**AiSuccessResponse**](../newai.md#model-aisuccessresponse) | - |
| **400** | &#x60;value&#x60; is missing or is not a boolean. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiSuccessResponse**](../newai.md#model-aisuccessresponse)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
