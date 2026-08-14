# aiProfilesCreate

Referenced types are defined in the [full reference](../newai.md).

> AiProfileMutationResult aiProfilesCreate(AiCreateProfileInput)

`POST /api/2.0/ai/profiles/create`

Create

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **AiCreateProfileInput** | body | [**AiCreateProfileInput**](../newai.md#model-aicreateprofileinput) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiProfileMutationResult**](../newai.md#model-aiprofilemutationresult) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiProfileMutationResult**](../newai.md#model-aiprofilemutationresult)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
