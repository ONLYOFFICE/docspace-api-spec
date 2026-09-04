# getThirdPartyAuthProviders

Referenced types are defined in the [full reference](../people.md).

> AccountInfoArrayWrapper getThirdPartyAuthProviders(inviteView, settingsView, clientCallback, fromOnly)

`GET /api/2.0/people/thirdparty/providers`

Get third-party accounts

Returns a list of the available third-party accounts.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **inviteView** | query | **Boolean** | Specifies whether to return providers that are available for invitation links, i.e. the user can login or register through these providers. | [optional] [example: false] |
| **settingsView** | query | **Boolean** | Specifies whether to display the provider settings in a pop-up window (true) or redirect them to the desktop application (false). | [optional] [example: false] |
| **clientCallback** | query | **String** | The method that is called after authentication. | [optional] [example: onAuthCallback] |
| **fromOnly** | query | **String** | The provider name if a response is required only from this provider. | [optional] [example: Google] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | List of third-party accounts | [**AccountInfoArrayWrapper**](../people.md#model-accountinfoarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../people.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../people.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../people.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**AccountInfoArrayWrapper**](../people.md#model-accountinfoarraywrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
