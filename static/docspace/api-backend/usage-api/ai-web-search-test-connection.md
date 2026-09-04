# aiWebSearchTestConnection

Referenced types are defined in the [full reference](../newai.md).

> aiProfilesTestConnection_200_response aiWebSearchTestConnection(AiWebSearchConfig)

`POST /api/2.0/ai/web-search/test-connection`

Test connection

Checks a web-search configuration against the live provider without storing it - for a Test button that must not commit on success.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **AiWebSearchConfig** | body | [**AiWebSearchConfig**](../newai.md#model-aiwebsearchconfig) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**aiProfilesTestConnection_200_response**](../newai.md#model-aiprofilestestconnection-200-response) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**aiProfilesTestConnection_200_response**](../newai.md#model-aiprofilestestconnection-200-response)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
