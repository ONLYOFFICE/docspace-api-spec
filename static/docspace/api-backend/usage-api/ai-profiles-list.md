# aiProfilesList

Referenced types are defined in the [full reference](../newai.md).

> List aiProfilesList()

`GET /api/2.0/ai/profiles/list`

List provider profiles

Lists the portal&#39;s AI provider profiles with their secrets stripped, the same way the single-profile read does. It takes no parameters and is not paginated, because a portal holds few profiles. On a portal running the AI gateway the answer is synthesised from the gateway&#39;s own catalogue rather than from stored records. The IDs in the answer are what the assignment operations and every round&#39;s &#x60;profileId&#x60; accept.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The portal&#39;s profiles, with their keys and headers stripped. | [**List**](../newai.md#model-aiprofile) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**List**](../newai.md#model-aiprofile)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
