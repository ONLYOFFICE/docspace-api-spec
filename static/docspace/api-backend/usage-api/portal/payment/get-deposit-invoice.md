# getDepositInvoice

> StringWrapper getDepositInvoice(id)

`GET /api/2.0/portal/payment/customer/deposits/{id}/invoice`

Get the top-up invoice

Hands back the address of the page on which the billing provider shows the invoice for one top-up of the  portal's wallet, so a client can open or download it. The top-up is named by the `id` that  `GET api/2.0/portal/payment/customer/deposits` returns, and only one listed there with `hasInvoice` true has an  invoice to show. Only the payer or the portal owner may read it, as with the billing account page, and the  call changes nothing. The address is absolute and points to the billing provider rather than to the portal;  it is asked for anew on every call, so request it when the user is about to open the invoice instead of  storing it. A top-up this portal does not have, one without an invoice, or a portal that is not a billing  customer answers 404, and an `id` that is not a number fails with 400. An installation without a billing  service answers 403, and 402 means the billing or the accounting service rejected the request or did not  answer, which a later retry may get past.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | path | **Long** (int64) | The ID of the top-up, taken from the `id` field of `GET api/2.0/portal/payment/customer/deposits`. | [required] [example: `15342`] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The absolute address of the hosted invoice page for the top-up | [**StringWrapper**](../../models/string-wrapper.md) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | `id` is not a number | - | - |
| **402** | The billing or the accounting service rejected the request for the top-up or its invoice link, or did not answer | - | - |
| **403** | The caller is neither the payer nor the portal owner, or the portal has no billing service configured | - | - |
| **404** | The portal has no billing customer, no top-up with this ID, or the top-up has no invoice | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../../models/error-api-response.md) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../../models/error-api-response.md) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../../models/error-api-response.md) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**StringWrapper**](../../models/string-wrapper.md)

## Authorization

[Basic](../portal.md#basic), [OAuth2](../portal.md#oauth2) (scopes: read, write), [ApiKeyBearer](../portal.md#apikeybearer), [asc_auth_key](../portal.md#asc_auth_key), [Bearer](../portal.md#bearer), [OpenId](../portal.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
