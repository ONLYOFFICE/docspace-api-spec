# sendCongratulations

> sendCongratulations(Userid, Key)

`POST /api/2.0/portal/sendcongratulations`

Send congratulations

Sends congratulations to the user after registering a portal.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **Userid** | query | **UUID** (uuid) | The user ID to receive the congratulatory message. | [required] [example: 00000000-0000-0000-0000-000000000000] |
| **Key** | query | **String** | The template identifier or email configuration key. | [required] [example: birthday] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Ok | - | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | No permissions to perform this action | - | - |
| **429** | Too Many Requests. | - | `Retry-After` |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

null (empty response body)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: Not defined
