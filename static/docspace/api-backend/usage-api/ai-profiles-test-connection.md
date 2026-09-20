# aiProfilesTestConnection

Referenced types are defined in the [full reference](../aichat.md).

> aiProfilesTestConnection_200_response aiProfilesTestConnection(body)

`POST /api/2.0/ai/profiles/test-connection`

Test a profile&#39;s provider

Probes a stored profile&#39;s credentials against its provider and reports the outcome in the answer, writing nothing - this is what a Test button calls so that a failure does not commit anything. &#x60;profileId&#x60; is required and may be sent in the body or as a query parameter. The result is carried in the body rather than in the status, so a failed probe still answers 200 and the caller has to read the payload. To validate credentials that are not stored yet, use &#x60;POST api/2.0/ai/profiles/list-provider-models&#x60;.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **body** | body | **String** | The ID of the profile to probe, as a bare JSON string. | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The outcome of the probe. A failed probe is reported here, not as a status. | [**aiProfilesTestConnection_200_response**](../aichat.md#model-aiprofilestestconnection-200-response) | - |
| **400** | &#x60;profileId&#x60; is missing. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../aichat.md#model-aierrorresponse) | - |

## Return type

[**aiProfilesTestConnection_200_response**](../aichat.md#model-aiprofilestestconnection-200-response)

## Authorization

[cookieAuth](../aichat.md#cookieauth), [bearerAuth](../aichat.md#bearerauth)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
