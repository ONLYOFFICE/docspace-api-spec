# getConsents

Referenced types are defined in the [full reference](../oauth.md).

> PageableModificationResponse getConsents(limit, last\_modified\_on)

`GET /api/2.0/clients/consents`

Retrieves a pageable list of consents

Retrieves a paginated list of user consents.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **limit** | query | **Integer** (int32) | Pagination limit | [required] [example: 1] [min: 1] [max: 50] |
| **last\_modified\_on** | query | **Date** (date-time) | Date of the last retrieved consent | [optional] [example: 2024-04-04T12:00:00Z] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Successfully retrieved user consents | [**PageableModificationResponse**](../oauth.md#model-pageablemodificationresponse) | - |

## Return type

[**PageableModificationResponse**](../oauth.md#model-pageablemodificationresponse)

## Authorization

[x-signature](../oauth.md#x-signature)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
