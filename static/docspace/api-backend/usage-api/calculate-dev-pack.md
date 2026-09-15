# calculateDevPack

Referenced types are defined in the [full reference](../api.md).

> PaymentCalculationWrapper calculateDevPack(DocsCloudDevPackRequestDto)

`POST /api/2.0/settings/docscloud/calculatedevpack`

Calculate the DocsCloudDevPack switch cost

Prices the upgrade of the paid DocsCloud subscription of the current portal to DocsCloudDevPack for  the requested number of users, without changing the subscription or charging anything. It applies the  same preconditions as the switch itself: the portal must hold an active DocsCloud subscription, must  not already hold a DocsCloudDevPack one, and its tariff must not be delayed or unpaid; the quotas and  the state of the current tariff are listed by &#x60;GET api/2.0/portal/tariff&#x60;. The caller must be a  DocSpace administrator of a portal registered with the billing service. The call is read-only and  idempotent, so it can be repeated for different quantities before any switch is made. It returns the  amount that switching would cost, the three-letter ISO 4217 currency of that amount, the quantity the  amount was calculated for, and the identifier of the billing operation; an empty result means the  billing service could not price the switch, which should then not be attempted. The switch itself is  performed by &#x60;POST api/2.0/settings/docscloud/switchtodevpack&#x60; with the same &#x60;quantity&#x60; and takes no  identifier from this response; to price a change in the number of users of a subscription the portal  already has, use &#x60;PUT api/2.0/portal/payment/calculatewallet&#x60; instead.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **DocsCloudDevPackRequestDto** | body | [**DocsCloudDevPackRequestDto**](../api.md#model-docsclouddevpackrequestdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The cost of switching to DocsCloudDevPack for the requested quantity, or an empty result if the billing service could not price it | [**PaymentCalculationWrapper**](../api.md#model-paymentcalculationwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The quantity is below the allowed minimum, the portal has no active DocsCloud subscription, or it already has a DocsCloudDevPack subscription | - | - |
| **402** | The portal tariff is delayed or not paid, so the switch cannot be priced | - | - |
| **403** | The caller is not a DocSpace administrator, or the billing service is not configured | - | - |
| **404** | The portal is not registered as a billing customer, or the DocsCloud and DocsCloudDevPack wallet products are not configured on this installation | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**PaymentCalculationWrapper**](../api.md#model-paymentcalculationwrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
