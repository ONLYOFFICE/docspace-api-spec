# getWhiteLabelLogos

Referenced types are defined in the [full reference](../api.md).

> WhiteLabelItemArrayWrapper getWhiteLabelLogos(IsDark, IsDefault)

`GET /api/2.0/settings/whitelabel/logos`

Get the white label logos

Returns the white label logos.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **IsDark** | query | **Boolean** | Specifies if the white label logo is for the dark theme or not. | [optional] [example: true] |
| **IsDefault** | query | **Boolean** | Specifies if the logo is for a default tenant or not. | [optional] [example: true] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | White label logos | [**WhiteLabelItemArrayWrapper**](../api.md#model-whitelabelitemarraywrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**WhiteLabelItemArrayWrapper**](../api.md#model-whitelabelitemarraywrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
