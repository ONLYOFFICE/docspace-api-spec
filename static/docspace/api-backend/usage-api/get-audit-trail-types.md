# getAuditTrailTypes

Referenced types are defined in the [full reference](../api.md).

> AuditTrailTypesWrapper getAuditTrailTypes()

`GET /api/2.0/security/audit/types`

Get audit trail types

Returns the vocabularies the audit filters are built from: &#x60;actions&#x60; lists every action the portal can record,  &#x60;actionTypes&#x60; the kinds of change they stand for, &#x60;productTypes&#x60; the products they belong to, &#x60;moduleTypes&#x60;  the locations inside those products, and &#x60;entryTypes&#x60; the kinds of entity an action can be applied to. The  caller needs the portal-settings right of a DocSpace administrator; the audit option of the pricing plan is  not required, so the lists can be read on any portal. The operation is read-only, takes no parameters and  depends on nothing else. Every value is the name to send in the matching query parameter of  &#x60;GET api/2.0/security/audit/events/filter&#x60; or &#x60;GET api/2.0/security/audit/login/filter&#x60;, so read this  operation once and reuse the answer instead of guessing spellings. The response is an untyped object holding  those five arrays of names, and it changes only with the portal version. Use  &#x60;GET api/2.0/security/audit/mappers&#x60; when the relations between products, modules and actions are needed  rather than the flat lists.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | The action, action type, product, module and entry type names accepted by the audit filters | [**AuditTrailTypesWrapper**](../api.md#model-audittrailtypeswrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **403** | The caller does not have the portal-settings right of a DocSpace administrator | - | - |
| **401** | Unauthorized | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **429** | Too Many Requests. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**AuditTrailTypesWrapper**](../api.md#model-audittrailtypeswrapper)

## Authorization

[Basic](../api.md#basic), [OAuth2](../api.md#oauth2) (scopes: read, write), [ApiKeyBearer](../api.md#apikeybearer), [asc_auth_key](../api.md#asc_auth_key), [Bearer](../api.md#bearer), [OpenId](../api.md#openid)

## HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json
