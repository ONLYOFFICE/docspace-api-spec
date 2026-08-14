# aiProfilesUpdate

Referenced types are defined in the [full reference](../newai.md).

> AiProfileMutationResult aiProfilesUpdate(AiProfile)

`PUT /api/2.0/ai/profiles/update`

Update

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **AiProfile** | body | [**AiProfile**](../newai.md#model-aiprofile) |  | [required] |

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

## AIPromptsApi
