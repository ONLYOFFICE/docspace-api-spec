# switchToDevPack

Referenced types are defined in the [full reference](../api.md).

> BooleanWrapper switchToDevPack(DocsCloudDevPackRequestDto)

`POST /api/2.0/settings/docscloud/switchtodevpack`

Switch DocsCloud to DocsCloudDevPack

Upgrades the paid DocsCloud subscription of the current portal to DocsCloudDevPack for the requested  number of users, charging the price difference to the portal wallet and moving the DocsCloud license  to the new product. The portal must hold an active DocsCloud subscription, must not already hold a  DocsCloudDevPack one, and its tariff must not be delayed or unpaid: the quotas and the state of the  current tariff are listed by &#x60;GET api/2.0/portal/tariff&#x60;, and the amount that will be charged is  returned by &#x60;POST api/2.0/settings/docscloud/calculatedevpack&#x60; for the same &#x60;quantity&#x60;. The caller  must be a DocSpace administrator of a portal registered with the billing service. The switch is  synchronous, mutating and not idempotent: repeating it after a successful call fails with 400, and  concurrent calls for one portal are serialized so that the wallet is charged only once. It returns  &#x60;true&#x60; when the subscription has been switched, and &#x60;false&#x60; when the billing service declines or  fails to perform the switch, in which case nothing is charged and the portal stays on DocsCloud.  Only the DocsCloud to DocsCloudDevPack direction is supported: to change the number of users of a  subscription the portal already has, or to schedule a reversion from DocsCloudDevPack back to  DocsCloud at the next billing period, use &#x60;PUT api/2.0/portal/payment/updatewallet&#x60; instead.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **DocsCloudDevPackRequestDto** | body | [**DocsCloudDevPackRequestDto**](../api.md#model-docsclouddevpackrequestdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Boolean value: true if the subscription is switched to DocsCloudDevPack, false if the billing service declines it | [**BooleanWrapper**](../api.md#model-booleanwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The quantity is below the allowed minimum, the portal has no active DocsCloud subscription, or it already has a DocsCloudDevPack subscription | - | - |
| **402** | The portal tariff is delayed or not paid, so the subscription cannot be switched | - | - |
| **403** | The caller is not a DocSpace administrator, or the billing service is not configured | - | - |
| **404** | The portal is not registered as a billing customer, or the DocsCloud and DocsCloudDevPack wallet products are not configured on this installation | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**BooleanWrapper**](../api.md#model-booleanwrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
