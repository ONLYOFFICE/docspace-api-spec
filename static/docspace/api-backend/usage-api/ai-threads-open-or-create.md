# aiThreadsOpenOrCreate

Referenced types are defined in the [full reference](../newai.md).

> AiOpenOrCreateResult aiThreadsOpenOrCreate(AiOpenOrCreateInput)

`POST /api/2.0/ai/threads/open-or-create`

Open or create

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **AiOpenOrCreateInput** | body | [**AiOpenOrCreateInput**](../newai.md#model-aiopenorcreateinput) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiOpenOrCreateResult**](../newai.md#model-aiopenorcreateresult) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiOpenOrCreateResult**](../newai.md#model-aiopenorcreateresult)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
