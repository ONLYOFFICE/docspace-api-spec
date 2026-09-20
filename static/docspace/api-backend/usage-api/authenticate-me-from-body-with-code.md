# authenticateMeFromBodyWithCode

Referenced types are defined in the [full reference](../api.md).

> AuthenticationTokenWrapper authenticateMeFromBodyWithCode(code, AuthWithCodeRequestsDto)

`POST /api/2.0/authentication/{code}`

Authenticate a user by code

Finishes a two-factor sign-in: checks the one-time code and, when it matches, issues the authentication token.  Call it only after &#x60;POST api/2.0/authentication&#x60; answered with &#x60;sms&#x60; or &#x60;tfa&#x60; set, and repeat the same  credentials in the body next to &#x60;code&#x60; - the code alone does not identify the user. The code comes from the  SMS the portal sent, which &#x60;POST api/2.0/authentication/sendsms&#x60; resends, or from the authenticator app;  whichever second factor the portal has enabled for this user is the one checked here. Open to unauthenticated  callers, mutating and not idempotent: a code is single-use, the sign-in is written to the login history, and  the first code accepted from an authenticator app also connects that app to the user. The answer carries  &#x60;token&#x60; for the &#x60;Authorization&#x60; header, &#x60;expires&#x60; unless &#x60;session&#x3D;true&#x60; tied the token to the browser session,  and either &#x60;sms&#x60; with the masked phone number or &#x60;tfa&#x60;. A wrong, empty or expired code fails with 401 and  counts against the brute-force limit, which then refuses further attempts with 403.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **code** | path | **String** | The two-factor authentication code. Send the same value as the &#x60;code&#x60; of the request body, which is the one the handler reads. | [required] |
| **AuthWithCodeRequestsDto** | body | [**AuthWithCodeRequestsDto**](../api.md#model-authwithcoderequestsdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The authentication token to send in the &#x60;Authorization&#x60; header, together with the second factor that was accepted | [**AuthenticationTokenWrapper**](../api.md#model-authenticationtokenwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The request body could not be validated, for example &#x60;confirmData.email&#x60; is not an email address | - | - |
| **401** | The credentials were rejected, or the two-factor code is wrong, empty or expired | - | - |
| **403** | The user is disabled, or too many failed attempts have blocked further sign-ins for these credentials | - | - |
| **404** | No user of this portal matches the credentials in the request body | - | - |
| **429** | The portal rate limiter rejected the call - retry after the interval in the &#x60;Retry-After&#x60; header | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**AuthenticationTokenWrapper**](../api.md#model-authenticationtokenwrapper)

## Authorization

[cookieAuth](../api.md#cookieauth), [bearerAuth](../api.md#bearerauth)

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json
