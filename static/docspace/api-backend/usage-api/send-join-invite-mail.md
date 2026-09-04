# sendJoinInviteMail

Referenced types are defined in the [full reference](../api.md).

> StringWrapper sendJoinInviteMail(AdminMessageBaseSettingsRequestsDto)

`POST /api/2.0/settings/sendjoininvite`

Sends an invitation email

Sends an invitation email with a link to the DocSpace.

## Parameters

|Name | In | Type | Description | Notes |
|------------- | ------------- | ------------- | ------------- | -------------|
| **AdminMessageBaseSettingsRequestsDto** | body | [**AdminMessageBaseSettingsRequestsDto**](../api.md#model-adminmessagebasesettingsrequestsdto) |  | [optional] |

## Responses

| Status code | Description | Type | Response headers |
|------------- | ------------- | ------------- | -------------|
| **200** | Message about sending a link to confirm joining the DocSpace | [**StringWrapper**](../api.md#model-stringwrapper) | `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset` |
| **400** | Incorrect email or email already exists | - | - |
| **403** | No permissions to perform this action | - | - |
| **405** | Joining the portal is not available | - | - |
| **429** | Request limit is exceeded | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | `Retry-After` |
| **500** | Internal Server Error. | [**ErrorApiResponse**](../api.md#model-errorapiresponse) | - |
| **502** | Bad Gateway. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |
| **503** | Service Unavailable. Returned by the reverse proxy, response body may be HTML and not JSON. | - | - |

## Return type

[**StringWrapper**](../api.md#model-stringwrapper)

## Authorization

No authorization required

## HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

## SettingsNotificationsApi
