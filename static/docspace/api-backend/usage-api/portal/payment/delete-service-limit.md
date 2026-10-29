# deleteServiceLimit

> deleteServiceLimit(id)

`DELETE /api/2.0/portal/payment/servicelimit/{id}`

Delete a service limit

Removes one spending limit on the AI services completely - the limit of the portal as a whole, the one for  every user, or a personal one - so it no longer restricts anyone. The portal needs a billing customer, and the  caller needs the permission to edit the portal settings as well as DocSpace administrator rights. The call is  destructive and cannot be undone: unlike switching a limit off with `PUT api/2.0/portal/payment/servicelimit`,  which keeps its settings, a deleted limit is gone, and a new one has to be created with  `POST api/2.0/portal/payment/servicelimit`. Deleting a personal limit lets the limit for every user apply to  that user. It is written to the portal audit trail. An ID that does not exist, belongs to another portal or is  not a limit on the AI services answers 404, which is also what a repeated deletion of the same limit gets.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **id** | path | **Integer** (int32) | The ID of the service limit, as returned in `id` by the operation that created it or by the reads of limits. | [required] [example: `42`] [min: 1] [max: 2147483647] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The service limit has been deleted; the response carries no content | - | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The ID is zero or negative | - | - |
| **403** | The caller may not edit the portal settings or is not a DocSpace administrator, or the portal has no billing service configured | - | - |
| **404** | The portal has no billing customer, or the portal has no limit on the AI services with this ID | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../../models/error-api-response.md) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../../models/error-api-response.md) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../../models/error-api-response.md) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

null (empty response body)

## Authorization

[Basic](../portal.md#basic), [OAuth2](../portal.md#oauth2) (scopes: read, write), [ApiKeyBearer](../portal.md#apikeybearer), [asc_auth_key](../portal.md#asc_auth_key), [Bearer](../portal.md#bearer), [OpenId](../portal.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
