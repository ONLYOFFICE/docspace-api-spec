# refreshLicense

Referenced types are defined in the [full reference](../api.md).

> BooleanWrapper refreshLicense()

`GET /api/2.0/settings/license/refresh`

Refresh the license

Re-reads the license file of this self-hosted Enterprise installation and rewrites the portal-wide quota and  tariff from it, so a file replaced on disk or a renewal issued by the vendor takes effect without a restart. A  license staged by &#x60;POST api/2.0/settings/license&#x60; is promoted to the active one here as well, but the usual  first-time order is upload and then &#x60;POST api/2.0/settings/license/accept&#x60;; this operation is for later  refreshes. The caller only has to be signed in - no administrator right is checked. Despite the &#x60;GET&#x60;, the  call rewrites stored data, and it is idempotent: repeating it applies the same license again. The editing  service is asked to confirm the license as part of the check, and the license it reports must match the file.  The answer is &#x60;true&#x60; when the license was applied and &#x60;false&#x60; on an installation with no license path  configured at all, such as a SaaS or open-source portal, where nothing is read and nothing changes. A missing  or unreadable file, a mismatched customer or edition, and an editing service that rejects the license all fail  the call instead of answering &#x60;false&#x60;. The operation stays reachable while the portal is unpaid.

## Parameters
This endpoint does not need any parameter.

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | &#x60;true&#x60; when the license file was re-read and the portal quota and tariff rewritten from it, &#x60;false&#x60; on an installation that has no license path configured | [**BooleanWrapper**](../api.md#model-booleanwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
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

- **Content-Type**: Not defined
- **Accept**: application/json
