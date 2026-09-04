# aiProfilesTestConnection

Referenced types are defined in the [full reference](../newai.md).

> aiProfilesTestConnection_200_response aiProfilesTestConnection(body)

`POST /api/2.0/ai/profiles/test-connection`

Test connection

Checks a stored profile&#39;s credentials against its provider and reports the provider&#39;s own error when the call fails. Nothing is written.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **body** | body | **String** |  | [required] |

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
