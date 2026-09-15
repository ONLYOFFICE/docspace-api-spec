# aiProfilesUpdate

Referenced types are defined in the [full reference](../newai.md).

> AiProfileMutationResult aiProfilesUpdate(AiProfile)

`PUT /api/2.0/ai/profiles/update`

Update a provider profile

Replaces a stored AI provider profile and returns it, re-checking name uniqueness and probing the credentials against the live provider again. The same two inputs are refused as on create - a private-network &#x60;baseUrl&#x60; and &#x60;providerType: external&#x60; - and the whole profile is overwritten by the one supplied rather than merged. On a portal running the AI gateway this answers 403, because profiles are managed centrally there. A profile that is bound to an action or an agent keeps those bindings.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **AiProfile** | body | [**AiProfile**](../newai.md#model-aiprofile) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Whether the profile was updated, with the stored profile in &#x60;profile&#x60;. | [**AiProfileMutationResult**](../newai.md#model-aiprofilemutationresult) | - |
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

## AIPromptsApi
