## Operation Scenarios
This document describes how to create, enable/disable, delete, and view API keys for sub-users and collaborators.
## Prerequisites
Log in to the CAM Console and go to [User List](https://console.cloud.tencent.com/cam). Find the sub-user or collaborator that needs to be configured and click **Username** to enter the user details page.
## Directions

### Creating API key for sub-account
You can create an API key for a sub-user/collaborator. After the API key is created, the sub-user/collaborator can use APIs, SDKs, or other development tools to manage the resources under the root account within the scope of the configured permissions.
1. On the user details page, click **API Key** to enter the API key management page.
2. On the API key management page, click **Create Key**.
 >
 > - Each sub-user/collaborator can have at most two API keys.
 > - An API key is an important credential for creating TencentCloud API requests. For the security of your assets and services, please keep the keys private, change them regularly, and delete old keys promptly after creating new ones.
 
### Viewing sub-account API key
You can view and copy the `SecretId` and `SecretKey` information of a sub-user/collaborator API key. The sub-user/collaborator can use the `SecretId` and `SecretKey` to use APIs, SDKs, or other development tools to manage resources under the root account within the scope of the configured permissions.
1. On the user details page, click **API Key** to enter the API key management page.
2. On the API key management page, perform the following operations to view and copy the `SecretId` and `SecretKey` information of the API key. An API key is an important credential for creating TencentCloud API requests. For the security of your assets and services, please keep the keys private, change them regularly, and delete old keys promptly after creating new ones.
 > - SecretId: this can be directly viewed in the "Key" column. Click ![](https://main.qcloudimg.com/raw/f76547dfc5a0b8982a714011026f3244.png) to copy and save it.
 > - SecretKey: click **Show** in the "Key" column. You will be able to view it after being authenticated. Click ![](https://main.qcloudimg.com/raw/f76547dfc5a0b8982a714011026f3244.png) to copy and save it.


### Disabling/Enabling sub-account API key
You can disable an API key of a sub-user/collaborator. Please do so with caution as Tencent Cloud will block all requests that use the API key after it is disabled.
1. On the user details page, click **API Key** to enter the API key management page.
2. On the API key management page, click **Disable** in the "Operation" column.
3. In the confirmation window that pops up, click **Confirm* to disable the access key.
>You can click **Enable** in the "Operation" column to enable the key. After the key is enabled, the sub-account/collaborator can use APIs, SDKs, or other development tools to manage the resources under the root account within the scope of the configured permissions.

### Deleting sub-account API key
1. On the user details page, click **API Key** to enter the API key management page.
2. On the API key management page, click **Disable** in the "Operation" column. If the API key that you want to delete has already been disabled, proceed to step 4.
3. In the confirmation window that pops up, click **Confirm**.
4. On the API key management page, click **Delete** in the "Operation" column to delete the API key.
>Please note that an API key cannot be recovered once deleted.

## Related Documents
For more information on how to query sub-account information through the `SecretId` of an access key, please see [Searching for Sub-users with Search Box](https://intl.cloud.tencent.com/document/product/598/32652) and [Searching for Collaborators with Search Box](https://intl.cloud.tencent.com/document/product/598/32643).
