# getClients

Referenced types are defined in the [full reference](../oauth.md).

> PageableResponse getClients(limit, last\_client\_id, last\_created\_on)

`GET /api/2.0/clients`

List clients

Retrieves a paginated list of OAuth2 clients. The results can be paginated using the limit parameter and last seen client ID/creation date.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **limit** | query | **Integer** (int32) | Pagination limit | [required] [example: 1] [default to 30] [min: 1] [max: 50] |
| **last\_client\_id** | query | **String** | ID of the last retrieved client | [optional] [example: 6c7cf17b-1bd3-47d5-94c6-be2d3570e168] |
| **last\_created\_on** | query | **Date** (date-time) | Date of the last retrieved client | [optional] [example: 2024-04-04T12:00:00Z] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Client list successfully retrieved | [**PageableResponse**](../oauth.md#model-pageableresponse) | - |
| **400** | Invalid pagination parameters | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
| **403** | Insufficient permissions to list clients | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
| **429** | Too many requests - rate limit exceeded | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
| **500** | Internal server error occurred | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |

## Return type

[**PageableResponse**](../oauth.md#model-pageableresponse)

## Authorization

[x-signature](../oauth.md#x-signature)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
