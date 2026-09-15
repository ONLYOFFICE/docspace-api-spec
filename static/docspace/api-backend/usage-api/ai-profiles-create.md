# aiProfilesCreate

Referenced types are defined in the [full reference](../newai.md).

> AiProfileMutationResult aiProfilesCreate(AiCreateProfileInput)

`POST /api/2.0/ai/profiles/create`

Create a provider profile

Creates an AI provider profile - the endpoint, credentials and model that a chat round runs on - and returns it. The name has to be unique, the credentials are probed against the live provider before anything is stored, and the portal&#39;s first profile also takes the &#x60;Default&#x60; assignment slot. Two inputs are refused outright: a &#x60;baseUrl&#x60; pointing at a private network address, and &#x60;providerType: external&#x60;, which delegates transport to the host application and therefore cannot work for a profile the server manages. On a portal running the AI gateway, profiles are managed centrally and this operation answers 403.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **AiCreateProfileInput** | body | [**AiCreateProfileInput**](../newai.md#model-aicreateprofileinput) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Whether the profile was created, with it in &#x60;profile&#x60;. A refusal is reported in &#x60;error&#x60; rather than as a status. | [**AiProfileMutationResult**](../newai.md#model-aiprofilemutationresult) | - |
| **400** | The provider URL is missing, malformed, or points at a private network address. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI profiles are read-only on this portal because they are managed by the AI gateway. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiProfileMutationResult**](../newai.md#model-aiprofilemutationresult)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
