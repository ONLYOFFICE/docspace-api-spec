# aiProfilesCreate

Referenced types are defined in the [full reference](../newai.md).

> AiProfileMutationResult aiProfilesCreate(AiCreateProfileInput)

`POST /api/2.0/ai/profiles/create`

Create

Creates an AI provider profile. The name must be unique and the credentials are validated against the provider before the profile is stored; the portal&#39;s first profile also takes the &#x60;Default&#x60; assignment slot.

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
