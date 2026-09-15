# aiWebSearchTestConnection

Referenced types are defined in the [full reference](../newai.md).

> aiProfilesTestConnection_200_response aiWebSearchTestConnection(AiWebSearchConfig)

`POST /api/2.0/ai/web-search/test-connection`

Test a web-search provider

Probes a web-search configuration against the live provider and reports the outcome, storing nothing - this is what a Test button calls so that a failure commits no state. The configuration is taken from the request rather than from storage, so credentials that were never saved can be checked. A &#x60;baseUrl&#x60; pointing at a private network address is refused before any request leaves the portal. The verdict is carried in the body rather than in the status, so a failed probe still answers 200 and the caller has to read the payload.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **AiWebSearchConfig** | body | [**AiWebSearchConfig**](../newai.md#model-aiwebsearchconfig) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The outcome of the probe. A failed probe is reported here, not as a status. | [**aiProfilesTestConnection_200_response**](../newai.md#model-aiprofilestestconnection-200-response) | - |
| **400** | The provider URL is missing, malformed, or points at a private network address. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**aiProfilesTestConnection_200_response**](../newai.md#model-aiprofilestestconnection-200-response)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
