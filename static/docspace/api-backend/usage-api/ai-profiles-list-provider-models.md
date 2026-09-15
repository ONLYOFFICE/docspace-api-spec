# aiProfilesListProviderModels

Referenced types are defined in the [full reference](../newai.md).

> List aiProfilesListProviderModels(aiProfilesListProviderModels\_request)

`POST /api/2.0/ai/profiles/list-provider-models`

List provider models

Lists the models an endpoint offers for credentials supplied in the request, before any profile exists - this is what a provider-setup form calls to fill its model picker. &#x60;providerType&#x60; and &#x60;baseUrl&#x60; are both required, and a 400 for either names the offending input in a &#x60;field&#x60; member so the form can highlight it; a &#x60;baseUrl&#x60; pointing at a private network address is refused as well. For &#x60;providerType: onlyoffice&#x60; the answer comes from the portal gateway&#39;s catalogue, which carries richer capability data than the provider&#39;s own listing and matches what &#x60;GET api/2.0/ai/profiles/list&#x60; reports; a portal without that gateway falls back to asking the provider. A provider that is unreachable or broken is reported as 502, and one that rejects the key as 400.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiProfilesListProviderModels\_request** | body | [**aiProfilesListProviderModels_request**](../newai.md#model-aiprofileslistprovidermodels-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The models the endpoint offers for the supplied credentials. | [**List**](../newai.md#model-aimodel) | - |
| **400** | &#x60;baseUrl&#x60; is missing, points at a private network address, or the provider rejected the supplied API key. | [**aiProfilesListProviderModels_400_response**](../newai.md#model-aiprofileslistprovidermodels-400-response) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **403** | AI is disabled for this portal, or the caller is a guest. Relayed from the DocSpace AI service. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **413** | The request body is larger than 100 KB, the JSON parser&#39;s limit on this route. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **500** | Unhandled failure. The reason is logged server-side and never echoed back. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |
| **502** | The AI provider could not be reached, or answered with a failure of its own. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**List**](../newai.md#model-aimodel)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
