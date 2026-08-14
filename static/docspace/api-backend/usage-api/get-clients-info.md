# getClientsInfo

Referenced types are defined in the [full reference](../oauth.md).

> PageableResponseClientInfoResponse getClientsInfo(limit, last\_client\_id, last\_created\_on)

`GET /api/2.0/clients/info`

Retrieves a pageable list of client information

Retrieves a paginated list of information for all clients.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **limit** | query | **Integer** (int32) | Pagination limit | [required] [example: 1] [min: 1] [max: 50] |
| **last\_client\_id** | query | **String** | ID of the last retrieved client | [optional] [example: 6c7cf17b-1bd3-47d5-94c6-be2d3570e168] |
| **last\_created\_on** | query | **Date** (date-time) | Date of the last retrieved client | [optional] [example: 2024-04-04T12:00:00Z] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Successfully retrieved clients info | [**PageableResponseClientInfoResponse**](../oauth.md#model-pageableresponseclientinforesponse) | - |
| **400** | Bad request | - | - |
| **429** | Too many requests | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
| **500** | Internal server error | - | - |

## Return type

[**PageableResponseClientInfoResponse**](../oauth.md#model-pageableresponseclientinforesponse)

## Authorization

[x-signature](../oauth.md#x-signature)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
