# aiProfilesGetById

Referenced types are defined in the [full reference](../newai.md).

> aiProfilesGetById_200_response aiProfilesGetById(id)

`GET /api/2.0/ai/profiles/get-by-id`

Get by id

Returns one AI provider profile, or an empty result when the identifier is unknown.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | query | **String** | The AI provider profile identifier. | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**aiProfilesGetById_200_response**](../newai.md#model-aiprofilesgetbyid-200-response) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**aiProfilesGetById_200_response**](../newai.md#model-aiprofilesgetbyid-200-response)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
