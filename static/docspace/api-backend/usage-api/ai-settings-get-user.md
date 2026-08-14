# aiSettingsGetUser

Referenced types are defined in the [full reference](../newai.md).

> AiAiUserSettingsWrapper aiSettingsGetUser()

`GET /api/2.0/ai/config/user`

Get user AI settings

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiAiUserSettingsWrapper**](../newai.md#model-aiaiusersettingswrapper) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiAiUserSettingsWrapper**](../newai.md#model-aiaiusersettingswrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
