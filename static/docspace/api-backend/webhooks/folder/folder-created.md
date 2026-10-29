# folder.created

> FolderDelivery folderCreated

`POST` to the URL of the subscription

Sent on the `folder.created` event. The body is a FolderDelivery, whose `payload` is a FolderPayload. Roles that may subscribe to it: `DocSpaceAdmin`, `RoomAdmin`, `User`.

Raised by these REST API operations:

- [`POST api/2.0/files/folder/{folderId}`](../../usage-api/files/folders/create-folder.md) (Create a folder)
- [`POST api/2.0/migration/migrate`](../../usage-api/migration/start-migration.md) (Start migration), for every folder the queued import creates, including the one in the personal section of each imported user that receives that user's files
- [`PUT api/2.0/people/delete`](../../usage-api/people/profiles/remove-users.md) (Delete users), for every deleted account that shared files or folders from its personal section, once the queued data deletion creates the folder in the caller's personal section that takes them over
- [`POST api/2.0/people/delete/personal/start`](../../usage-api/people/user-data/start-delete-personal-folder.md) (Delete the personal folder), once the queued job creates the folder that takes over the files and folders the caller shared from the personal folder, in the personal section of the member who last changed that folder or of the portal owner; not when the caller shared none
- [`POST api/2.0/people/reassign/start`](../../usage-api/people/user-data/start-reassign.md) (Start the data reassignment), once the queued reassignment creates the folder in the recipient's personal section that takes over the files and folders the source account shared from its own; not when it shared none
- [`POST api/2.0/people/remove/start`](../../usage-api/people/user-data/start-remove.md) (Start the data deletion), once the queued data deletion creates the folder in the caller's personal section that takes over the files and folders the account shared from its own; not when it shared none
- [`DELETE api/2.0/people/{userId}`](../../usage-api/people/profiles/delete-member.md) (Delete a user), once the queued data deletion creates the folder in the caller's personal section that takes over the files and folders the account shared from its own; not when it shared none

Also raised by the automatic clean-up of a guest's personal folder left unchanged for 30 days, once for the folder it creates in the personal section of the member who takes over the files and folders the guest shared from it.

## Request headers

| Name | Description |
|------------- | -------------|
| **x-docspace-signature-256** | `sha256=` and the uppercase hex HMAC-SHA256 of the raw body under the subscription's secret. The only header that is authenticated; compare it case-insensitively. |
| **x-docspace-event-id** | A copy of `event.id`, for dropping an already-seen delivery without parsing the body. Not covered by the signature. |
| **x-docspace-event-timestamp** | A copy of `event.createOn`, in the same ISO-8601 UTC spelling. Not covered by the signature. |

## Request body

[**FolderDelivery**](../models/folder-delivery.md)

## Responses

| Status code | Description |
|------------- | -------------|
| **2XX** | Acknowledges the delivery. The answer's body is kept in the delivery log, not interpreted. |
| **410** | Deletes the subscription at once; nothing is retried or sent to it any more. |
| **default** | Any other status, a redirect, a timeout or a network error fails the attempt, which is retried on the schedule the description of this document gives. |

## HTTP request headers

- **Content-Type**: application/json
