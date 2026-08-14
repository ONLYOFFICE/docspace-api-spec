# aiProfilesGetById

Referenced types are defined in the [full reference](../newai.md).

> AiProfile aiProfilesGetById(id)

`GET /api/2.0/ai/profiles/get-by-id`

Get by id

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | query | **String** |  | [required] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Success. | [**AiProfile**](../newai.md#model-aiprofile) | - |
| **401** | Missing &#x60;asc_auth_key&#x60; cookie or &#x60;Authorization&#x60; header. | [**AiErrorResponse**](../newai.md#model-aierrorresponse) | - |

## Return type

[**AiProfile**](../newai.md#model-aiprofile)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
