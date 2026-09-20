# authenticateMe

Referenced types are defined in the [full reference](../api.md).

> AuthenticationTokenWrapper authenticateMe(AuthRequestsDto)

`POST /api/2.0/authentication`

Authenticate a user

Signs a user in to the current portal and either issues the authentication token or reports which second  factor is still missing. Credentials go in the body as &#x60;userName&#x60; with &#x60;password&#x60; or &#x60;passwordHash&#x60;, as the  key of a confirmation link in &#x60;confirmData&#x60;, or as a third-party account (&#x60;provider&#x60; with &#x60;accessToken&#x60;, or  &#x60;serializedProfile&#x60;), which only a standalone installation or a tariff with third-party sign-in allows. Open  to unauthenticated callers, mutating and not  idempotent: it writes a login event, sets the portal cookies and counts every failure against the brute-force  limit. When a second factor is required for this user the answer carries no &#x60;token&#x60; but &#x60;sms&#x60; with the masked  phone number - or a &#x60;confirmUrl&#x60; pointing at &#x60;POST api/2.0/authentication/setphone&#x60; while no number is  activated yet - or &#x60;tfa&#x60; with the setup key while the authenticator app is not connected; submit the code to  &#x60;POST api/2.0/authentication/{code}&#x60; to finish such a sign-in. Otherwise the answer carries &#x60;token&#x60; for the  &#x60;Authorization&#x60; header and &#x60;expires&#x60;, which is omitted when &#x60;session&#x3D;true&#x60; ties the token to the browser  session. An unknown user fails with 404, rejected credentials with 401, a disabled or blocked user with 403.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **AuthRequestsDto** | body | [**AuthRequestsDto**](../api.md#model-authrequestsdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The authentication token, or the second factor that has to be passed before a token is issued | [**AuthenticationTokenWrapper**](../api.md#model-authenticationtokenwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | The request body could not be validated, for example &#x60;confirmData.email&#x60; is not an email address | - | - |
| **401** | The password, the confirmation key or the third-party profile was rejected, or third-party sign-in is not allowed for this portal | - | - |
| **403** | The user is disabled, or too many failed attempts and CAPTCHA failures have blocked further sign-ins for these credentials | - | - |
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
