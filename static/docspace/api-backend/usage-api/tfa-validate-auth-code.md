# tfaValidateAuthCode

Referenced types are defined in the [full reference](../api.md).

> BooleanWrapper tfaValidateAuthCode(TfaValidateRequestsDto)

`POST /api/2.0/settings/tfaapp/validate`

Validate the TFA code

Verifies a two-factor authentication code for the account named in the confirmation link being used, and  completes that account&#39;s pending TFA step. The call is reachable only with a confirmation token carrying the  &#x60;TfaActivation&#x60; or &#x60;TfaAuth&#x60; role, issued by &#x60;GET api/2.0/settings/tfaapp/confirm&#x60; or by the login flow; an  ordinary bearer token is refused. Both a code from the authenticator application and one of the account&#39;s  unused backup codes are accepted, and a backup code is spent by the check. The call mutates state: it signs  the account in, clears the confirmation cookie so the link cannot be replayed, and on the very first  activation it generates the backup codes later returned by &#x60;GET api/2.0/settings/tfaappcodes&#x60;. Pass  &#x60;session&#x3D;true&#x60; to keep that sign-in for the browser session only instead of a persistent one. It answers  &#x60;true&#x60; only for that first activation and &#x60;false&#x60; when an application was already linked. A wrong code is  rejected as an invalid request, and further attempts are refused once the portal&#39;s login attempt limit is  reached. The call also works while the portal&#39;s payment is overdue.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **TfaValidateRequestsDto** | body | [**TfaValidateRequestsDto**](../api.md#model-tfavalidaterequestsdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | &#x60;true&#x60; when the code completed a first activation and backup codes were generated, &#x60;false&#x60; when an application was already linked | [**BooleanWrapper**](../api.md#model-booleanwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **400** | Bad Request. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**BooleanWrapper**](../api.md#model-booleanwrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
