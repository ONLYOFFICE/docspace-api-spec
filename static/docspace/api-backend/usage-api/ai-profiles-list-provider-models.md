# aiProfilesListProviderModels

Referenced types are defined in the [full reference](../newai.md).

> List aiProfilesListProviderModels(aiProfilesListProviderModels\_request)

`POST /api/2.0/ai/profiles/list-provider-models`

List provider models

Lists the models a provider offers for the supplied endpoint and key, before any profile is created from them.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **aiProfilesListProviderModels\_request** | body | [**aiProfilesListProviderModels_request**](../newai.md#model-aiprofileslistprovidermodels-request-body) |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**List**](../newai.md#model-aimodel) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**List**](../newai.md#model-aimodel)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
