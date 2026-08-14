# getClientInfo

Referenced types are defined in the [full reference](../oauth.md).

> ClientInfoResponse getClientInfo(clientId)

`GET /api/2.0/clients/{clientId}/info`

Retrieves detailed information for a specific client

Retrieves the detailed information for a client with the ID specified in the request.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **clientId** | path | **String** | ID of the client to retrieve | [required] [example: 6c7cf17b-1bd3-47d5-94c6-be2d3570e168] [minLength: 1] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Successfully retrieved client info | [**ClientInfoResponse**](../oauth.md#model-clientinforesponse) | - |
| **400** | Bad request | - | - |
| **429** | Too many requests | [**ProblemDetail**](../oauth.md#model-problemdetail) | - |
| **500** | Internal server error | - | - |

## Return type

[**ClientInfoResponse**](../oauth.md#model-clientinforesponse)

## Authorization

[x-signature](../oauth.md#x-signature)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
