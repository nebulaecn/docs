---
description: This chapter describes the process of authentication by API.
---

# Authenticating

You can see this process for UI using the link to the User Guide below:‌

​Authentication Guide​‌

## Confirm code <a id="barong"></a>

‌

#### /api/v2/auth/identity/users/password/confirm\_code <a id="api-v2-barong-identity-users-password-confirm_code"></a>

‌

**POST**‌

**Description**‌

Sets new account password‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| reset\_password\_token | formData | Token from email | Yes | string |
| password | formData | User password | Yes | string |
| confirm\_password | formData | User password | Yes | string |

‌

**Responses**

| Code | Description |
| :--- | :--- |
| 201 | Resets password |
| 400 | Required params are empty |
| 404 | Record is not found |
| 422 | Validation errors |

‌

#### /api/v2/auth/identity/users/password/generate\_code <a id="api-v2-barong-identity-users-password-generate_code"></a>

‌

**POST**‌

**Description**‌

Send password reset instructions‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| email | formData | Account email | Yes | string |
| captcha\_response | formData | Response from captcha widget | No | string |

‌

**Responses**

| Code | Description |
| :--- | :--- |
| 201 | Generated password reset code |
| 400 | Required params are missing |
| 404 | User doesn't exist |
| 422 | Validation errors |

‌

#### /api/v2/auth/identity/users/email/confirm\_code <a id="api-v2-barong-identity-users-email-confirm_code"></a>

‌

**POST**‌

**Description**‌

Confirms an account‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| token | formData | Token from email | Yes | string |

‌

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 201 | Confirms an account | API\_V2\_Entities\_UserWithFullInfo |
| 400 | Required params are missing | ​Content |
| 422 | Validation errors | ​Content |

‌

#### /api/v2/auth/identity/users/email/generate\_code <a id="api-v2-barong-identity-users-email-generate_code"></a>

‌

**POST**‌

**Description**‌

Send confirmations instructions‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| email | formData | Account email | Yes | string |
| captcha\_response | formData | Response from captcha widget | No | string |

‌

**Responses**

| Code | Description |
| :--- | :--- |
| 201 | Generated verification code |
| 400 | Required params are missing |
| 422 | Validation errors |

‌

#### /api/v2/auth/identity/users/register\_geetest <a id="api-v2-barong-identity-users-register_geetest"></a>

‌

**GET**‌

**Description**‌

Register Geetest captcha‌

**Responses**

| Code | Description |
| :--- | :--- |
| 200 | Register Geetest captcha |

‌

#### /api/v2/auth/identity/users <a id="api-v2-barong-identity-users"></a>

‌

**POST**‌

**Description**‌

Creates new user‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| email | formData | User Email | Yes | string |
| password | formData | User Password | Yes | string |
| username | formData | User Username | No | string |
| refid | formData | Referral uid | No | string |
| captcha\_response | formData | Response from captcha widget | No | string |
| data | formData | Any additional key: value pairs in json string format | No | string |

‌

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 201 | Creates new user | API\_V2\_Entities\_UserWithFullInfo |
| 400 | Required params are missing | ​Content |
| 422 | Validation errors | ​Content |

‌

#### /api/v2/auth/identity/users/access <a id="api-v2-barong-identity-users-access"></a>

‌

**POST**‌

**Description**‌

Creates new whitelist restriction‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| whitelink\_token | formData | ​Content | Yes | string |

‌

**Responses**

| Code | Description |
| :--- | :--- |
| 200 | Whitelist restriction was created |
| 400 | Required params are missing |
| 422 | Validation errors |

‌

#### /api/v2/auth/identity/sessions/auth0 <a id="api-v2-barong-identity-sessions-auth0"></a>

‌

**POST**‌

**Description**‌

Auth0 authentication by id\_token‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| id\_token | formData | ID Token | Yes | string |

‌

**Responses**

| Code | Description |
| :--- | :--- |
| 200 | User authenticated |
| 400 | Required params are empty |
| 404 | Record is not found |

‌

#### /api/v2/auth/identity/sessions <a id="api-v2-barong-identity-sessions"></a>

‌

**DELETE**‌

**Description**‌

Destroy current session‌

**Responses**

| Code | Description |
| :--- | :--- |
| 204 | Session was destroyed |
| 400 | Required params are empty |
| 404 | Record is not found |

‌

#### POST‌

**Description**‌

Start a new session‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| email | formData | ​Content | Yes | string |
| password | formData | ​Content | Yes | string |
| captcha\_response | formData | Response from captcha widget | No | string |
| otp\_code | formData | Code from Google Authenticator | No | string |

‌

**Responses**

| Code | Description |
| :--- | :--- |
| 201 | Start a new session |
| 400 | Required params are empty |
| 404 | Record is not found |

‌

#### /api/v2/auth/identity/configs <a id="api-v2-barong-identity-configs"></a>

‌

**GET**‌

**Description**‌

Get auth configurations‌

**Responses**

| Code | Description |
| :--- | :--- |
| 200 | Get auth configurations |

‌

#### /api/v2/auth/identity/version <a id="api-v2-barong-identity-version"></a>

‌

**GET**‌

**Description**‌

Get auth version‌

**Responses**

| Code | Description |
| :--- | :--- |
| 200 | Get auth version |

‌

#### /api/v2/auth/identity/time <a id="api-v2-barong-identity-time"></a>

‌

**GET**‌

**Description**‌

Get server current unix timestamp.‌

**Responses**

| Code | Description |
| :--- | :--- |
| 200 | Get server current unix timestamp. |

‌

#### /api/v2/auth/identity/ping <a id="api-v2-barong-identity-ping"></a>

‌

**GET**‌

**Description**‌

Test connectivity‌

**Responses**

| Code | Description |
| :--- | :--- |
| 200 | Test connectivity |

‌

#### /api/v2/auth/identity/password/validate <a id="api-v2-barong-identity-password-validate"></a>

‌

**POST**‌

**Description**‌

Password strength testing‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| password | formData | User password | Yes | string |

‌

**Responses**

| Code | Description |
| :--- | :--- |
| 201 | Password strength testing |

‌

#### /api/v2/auth/resource/swagger\_doc/{name} <a id="api-v2-barong-resource-swagger_doc-name"></a>

‌

**GET**‌

**Description**‌

Swagger compatible API description for specific API‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| name | path | Resource name of mounted API | Yes | string |
| locale | query | Locale of API documentation | No | string |

‌

**Responses**

| Code | Description |
| :--- | :--- |
| 200 | Swagger compatible API description for specific API |

‌

#### /api/v2/auth/resource/swagger\_doc <a id="api-v2-barong-resource-swagger_doc"></a>

‌

**GET**‌

**Description**‌

Swagger compatible API description‌

**Responses**

| Code | Description |
| :--- | :--- |
| 200 | Swagger compatible API description |

‌

#### /api/v2/auth/resource/service\_accounts/api\_keys/{kid} <a id="api-v2-barong-resource-service_accounts-api_keys-kid"></a>

‌

**PUT**‌

**Description**‌

Updates an api key‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| service\_account\_uid | formData | ​Content | Yes | string |
| kid | path | Service account kid | Yes | string |
| scope | formData | Comma separated scopes | No | string |
| state | formData | State of API Key. "active" state means key is active and can be used for auth | No | string |
| totp\_code | formData | Code from Google Authenticator | Yes | string |

‌

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Updates an api key | API\_V2\_Entities\_APIKey |
| 400 | Required params are empty | ​Content |
| 401 | Invalid bearer token | ​Content |
| 404 | Record is not found | ​Content |
| 422 | Validation errors | ​Content |

‌

**DELETE**‌

**Description**‌

Delete an api key for specific service account‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| service\_account\_uid | query | ​Content | Yes | string |
| kid | path | Service account kid | Yes | string |
| totp\_code | query | Code from Google Authenticator | Yes | string |

‌

**Responses**

| Code | Description |
| :--- | :--- |
| 204 | Succefully deleted |
| 400 | Required params are empty |
| 401 | Invalid bearer token |
| 404 | Record is not found |

‌

#### /api/v2/auth/resource/service\_accounts/api\_keys <a id="api-v2-barong-resource-service_accounts-api_keys"></a>

‌

**POST**‌

**Description**‌

Create api key for specific service account.‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| service\_account\_uid | formData | ​Content | Yes | string |
| algorithm | formData | Service account algorithm | Yes | string |
| scope | formData | Comma separated scopes | No | string |
| totp\_code | formData | Code from Google Authenticator | Yes | string |

‌

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 201 | Create api key for specific service account. | API\_V2\_Entities\_APIKey |
| 400 | Require 2FA and totp code | ​Content |
| 401 | Invalid bearer token | ​Content |

‌

**GET**‌

**Description**‌

List all api keys for specific service account.‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| ordering | query | If set, returned values will be sorted in specific order, defaults to 'asc'. | No | string |
| order\_by | query | Name of the field, which result will be ordered by. | No | string |
| page | query | Page number \(defaults to 1\). | No | integer |
| limit | query | Number of users per page \(defaults to 100, maximum is 100\). | No | integer |
| service\_account\_uid | query | ​Content | Yes | string |

‌

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | List all api keys for specific service account. | API\_V2\_Entities\_APIKey |
| 400 | Require 2FA and totp code | ​Content |
| 401 | Invalid bearer token | ​Content |

‌

#### /api/v2/auth/resource/service\_accounts <a id="api-v2-barong-resource-service_accounts"></a>

‌

**GET**‌

**Description**‌

List all service accounts for current user.‌

**Responses**

| Code | Description |
| :--- | :--- |
| 200 | List all service accounts for current user. |
| 400 | Require 2FA and totp code |
| 401 | Invalid bearer token |

‌

**Security**

| Security Schema | Scopes |
| :--- | :--- |
| BearerToken | ​Content |

‌

#### /api/v2/auth/resource/data\_storage <a id="api-v2-barong-resource-data_storage"></a>

‌

**POST**‌

**Description**‌

Create data storage‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| title | formData | Storage title | Yes | string |
| data | formData | Storage data | Yes | string |

‌

**Responses**

| Code | Description |
| :--- | :--- |
| 201 | Data Storage was created |
| 401 | Invalid bearer token |
| 422 | Validation errors |

‌

#### /api/v2/auth/resource/api\_keys <a id="api-v2-barong-resource-api_keys"></a>

‌

**GET**‌

**Description**‌

List all api keys for current account.‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| ordering | query | If set, returned values will be sorted in specific order, defaults to 'asc'. | No | string |
| order\_by | query | Name of the field, which result will be ordered by. | No | string |
| page | query | Page number \(defaults to 1\). | No | integer |
| limit | query | Number of users per page \(defaults to 100, maximum is 100\). | No | integer |

‌

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | List all api keys for current account. | API\_V2\_Entities\_APIKey |
| 400 | Require 2FA and totp code | ​Content |
| 401 | Invalid bearer token | ​Content |

‌

**POST**‌

**Description**‌

Create an api key‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| algorithm | formData | API key algorithm | Yes | string |
| scope | formData | Comma separated scopes | No | string |
| totp\_code | formData | Code from Google Authenticator | Yes | string |

‌

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 201 | Create an api key | API\_V2\_Entities\_APIKey |
| 400 | Required params are empty | ​Content |
| 401 | Invalid bearer token | ​Content |
| 422 | Validation errors | ​Content |

‌

#### /api/v2/auth/resource/api\_keys/{kid} <a id="api-v2-barong-resource-api_keys-kid"></a>

‌

**DELETE**‌

**Description**‌

Delete an api key‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| kid | path | API key kid | Yes | string |
| totp\_code | query | Code from Google Authenticator | Yes | string |

‌

**Responses**

| Code | Description |
| :--- | :--- |
| 204 | Succefully deleted |
| 400 | Required params are empty |
| 401 | Invalid bearer token |
| 404 | Record is not found |

‌

**PATCH**‌

**Description**‌

Updates an api key‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| kid | path | API key kid | Yes | string |
| scope | formData | Comma separated scopes | No | string |
| state | formData | State of API Key. "active" state means key is active and can be used for auth | No | string |
| totp\_code | formData | Code from Google Authenticator | Yes | string |

‌

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Updates an api key | API\_V2\_Entities\_APIKey |
| 400 | Required params are empty | ​Content |
| 401 | Invalid bearer token | ​Content |
| 404 | Record is not found | ​Content |
| 422 | Validation errors | ​Content |

‌

#### /api/v2/auth/resource/otp/verify <a id="api-v2-barong-resource-otp-verify"></a>

‌

**POST**‌

**Description**‌

Verify 2FA code‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| code | formData | Code from Google Authenticator | Yes | string |

‌

**Responses**

| Code | Description |
| :--- | :--- |
| 200 | 2FA was verified |
| 400 | 2FA has not been enabled for this account or code is missing |
| 401 | Invalid bearer token |
| 422 | Validation errors |

‌

#### /api/v2/auth/resource/otp/disable <a id="api-v2-barong-resource-otp-disable"></a>

‌

**POST**‌

**Description**‌

Disable 2FA‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| code | formData | Code from Google Authenticator | Yes | string |

‌

**Responses**

| Code | Description |
| :--- | :--- |
| 200 | 2FA was disabled |
| 400 | 2FA has not been enabled for this account or code is missing |
| 401 | Invalid bearer token |
| 422 | Validation errors |

‌

#### /api/v2/auth/resource/otp/enable <a id="api-v2-barong-resource-otp-enable"></a>

‌

**POST**‌

**Description**‌

Enable 2FA‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| code | formData | Code from Google Authenticator | Yes | string |

‌

**Responses**

| Code | Description |
| :--- | :--- |
| 200 | 2FA was enabled |
| 400 | 2FA has been enabled for this account or code is missing |
| 401 | Invalid bearer token |
| 422 | Validation errors |

‌

#### /api/v2/auth/resource/otp/generate\_qrcode <a id="api-v2-barong-resource-otp-generate_qrcode"></a>

‌

**POST**‌

**Description**‌

Generate qr code for 2FA‌

**Responses**

| Code | Description |
| :--- | :--- |
| 200 | QR code was generated |
| 400 | 2FA has been enabled for this account |
| 401 | Invalid bearer token |

‌

#### /api/v2/auth/resource/phones/verify <a id="api-v2-barong-resource-phones-verify"></a>

‌

**POST**‌

**Description**‌

Verify a phone‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| phone\_number | formData | Phone number with country code | Yes | string |
| verification\_code | formData | Verification code from sms | Yes | string |

‌

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 201 | Verify a phone | API\_V2\_Entities\_UserWithFullInfo |
| 400 | Required params are empty | ​Content |
| 401 | Invalid bearer token | ​Content |
| 404 | Record is not found | ​Content |

‌

#### /api/v2/auth/resource/phones/send\_code <a id="api-v2-barong-resource-phones-send_code"></a>

‌

**POST**‌

**Description**‌

Resend activation code‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| phone\_number | formData | Phone number with country code | Yes | string |
| channel | formData | The verification method to use | No | string |

‌

**Responses**

| Code | Description |
| :--- | :--- |
| 200 | Activation code was resend |
| 400 | Required params are empty |
| 401 | Invalid bearer token |
| 404 | Record is not found |
| 422 | Validation errors |

‌

#### /api/v2/auth/resource/phones <a id="api-v2-barong-resource-phones"></a>

‌

**POST**‌

**Description**‌

Add new phone‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| phone\_number | formData | Phone number with country code | Yes | string |
| channel | formData | The verification method to use | No | string |

‌

**Responses**

| Code | Description |
| :--- | :--- |
| 200 | New phone was added |
| 400 | Required params are empty |
| 401 | Invalid bearer token |
| 404 | Record is not found |
| 422 | Validation errors |

‌

**GET**‌

**Description**‌

Returns list of user's phones‌

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Returns list of user's phones | API\_V2\_Entities\_Phone |
| 401 | Invalid bearer token | ​Content |

‌

#### /api/v2/auth/resource/documents <a id="api-v2-barong-resource-documents"></a>

‌

**POST**‌

**Description**‌

Upload a new document for current user‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| doc\_type | formData | Document type | Yes | string |
| doc\_number | formData | Document number | Yes | string |
| upload | formData | Array of Rack::Multipart::UploadedFile | Yes | string |
| doc\_expire | formData | Document expiration date | No | date |
| doc\_category | formData | Category of the submitted document - front/back/selfie etc. | No | string |
| identificator | formData | Identificator for documents to be supplied together | No | string |
| metadata | formData | Any additional key: value pairs in json string format | No | string |

‌

**Responses**

| Code | Description |
| :--- | :--- |
| 201 | Document is uploaded |
| 400 | Required params are empty |
| 401 | Invalid bearer token |
| 422 | Validation errors |

‌

**GET**‌

**Description**‌

Return current user documents list‌

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Return current user documents list | API\_V2\_Entities\_Document |
| 401 | Invalid bearer token | ​Content |

‌

#### /api/v2/auth/resource/profiles <a id="api-v2-barong-resource-profiles"></a>

‌

**PUT**‌

**Description**‌

Update a profile for current\_user‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| first\_name | formData | First Name | No | string |
| last\_name | formData | Last Name | No | string |
| dob | formData | Date of Birth | No | date |
| address | formData | Address | No | string |
| postcode | formData | Postcode | No | string |
| city | formData | City | No | string |
| country | formData | Country | No | string |
| metadata | formData | Any additional key: value pairs in json string format | No | string |
| confirm | formData | Profile confirmation | No | boolean |

‌

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Update a profile for current\_user | API\_V2\_Entities\_Profile |
| 401 | Invalid bearer token | ​Content |
| 422 | Validation errors | ​Content |

‌

**POST**‌

**Description**‌

Create a profile for current\_user‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| first\_name | formData | First Name | No | string |
| last\_name | formData | Last Name | No | string |
| dob | formData | Date of Birth | No | date |
| address | formData | Address | No | string |
| postcode | formData | Postcode | No | string |
| city | formData | City | No | string |
| country | formData | Country | No | string |
| metadata | formData | Any additional key: value pairs in json string format | No | string |
| confirm | formData | Profile confirmation | No | boolean |

‌

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 201 | Create a profile for current\_user | API\_V2\_Entities\_Profile |
| 400 | Required params are empty | ​Content |
| 401 | Invalid bearer token | ​Content |
| 409 | Profile already exists | ​Content |
| 422 | Validation errors | ​Content |

‌

#### /api/v2/auth/resource/profiles/me <a id="api-v2-barong-resource-profiles-me"></a>

‌

**GET**‌

**Description**‌

Return profiles of current resource owner‌

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Return profiles of current resource owner | API\_V2\_Entities\_Profile |
| 401 | Invalid bearer token | ​Content |
| 404 | User has no profile | ​Content |

‌

#### /api/v2/auth/resource/labels/{key} <a id="api-v2-barong-resource-labels-key"></a>

‌

**DELETE**‌

**Description**‌

Delete a label with 'public' scope.‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| key | path | Label key. | Yes | string |

‌

**Responses**

| Code | Description |
| :--- | :--- |
| 204 | Succefully deleted |
| 400 | Required params are empty |
| 401 | Invalid bearer token |
| 404 | Record is not found |

‌

**PATCH**‌

**Description**‌

Update a label with 'public' scope.‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| key | path | Label key. | Yes | string |
| value | formData | Label value. | Yes | string |

‌

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Update a label with 'public' scope. | API\_V2\_Entities\_Label |
| 400 | Required params are empty | ​Content |
| 401 | Invalid bearer token | ​Content |
| 404 | Record is not found | ​Content |
| 422 | Validation errors | ​Content |

‌

**GET**‌

**Description**‌

Return a label by key.‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| key | path | Label key. | Yes | string |

‌

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Return a label by key. | API\_V2\_Entities\_Label |
| 400 | Required params are empty | ​Content |
| 401 | Invalid bearer token | ​Content |
| 404 | Record is not found | ​Content |

‌

#### /api/v2/auth/resource/labels <a id="api-v2-barong-resource-labels"></a>

‌

**POST**‌

**Description**‌

Create a label with 'public' scope.‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| key | formData | Label key. | Yes | string |
| value | formData | Label value. | Yes | string |

‌

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 201 | Create a label with 'public' scope. | API\_V2\_Entities\_Label |
| 400 | Required params are empty | ​Content |
| 401 | Invalid bearer token | ​Content |
| 422 | Validation errors | ​Content |

‌

**GET**‌

**Description**‌

List all labels for current user.‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| ordering | query | If set, returned labels sorted in specific order, default to "asc". | No | string |

‌

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | List all labels for current user. | API\_V2\_Entities\_Label |
| 401 | Invalid bearer token | ​Content |

‌

#### /api/v2/auth/resource/users/password <a id="api-v2-barong-resource-users-password"></a>

‌

**PUT**‌

**Description**‌

Sets new account password‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| old\_password | formData | Previous account password | Yes | string |
| new\_password | formData | User password | Yes | string |
| confirm\_password | formData | User password | Yes | string |

‌

**Responses**

| Code | Description |
| :--- | :--- |
| 201 | Changes password |
| 400 | Required params are empty |
| 404 | Record is not found |
| 422 | Validation errors |

‌

#### /api/v2/auth/resource/users/activity/{topic} <a id="api-v2-barong-resource-users-activity-topic"></a>

‌

**GET**‌

**Description**‌

Returns user activity‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| topic | path | Topic of user activity. Allowed: \[all, password, session, otp\] | Yes | string |
| time\_from | query | An integer represents the seconds elapsed since Unix epoch.If set, only activities created after the time will be returned. | No | integer |
| time\_to | query | An integer represents the seconds elapsed since Unix epoch.If set, only activities created before the time will be returned. | No | integer |
| result | query | Result of user activity. Allowed: \[succeed, failed, denied\] | No | string |
| page | query | Page number \(defaults to 1\). | No | integer |
| limit | query | Number of users per page \(defaults to 100, maximum is 100\). | No | integer |

‌

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Returns user activity | API\_V2\_Entities\_Activity |

‌

#### /api/v2/auth/resource/users/me <a id="api-v2-barong-resource-users-me"></a>

‌

**DELETE**‌

**Description**‌

Blocks current user‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| password | query | Account password | Yes | string |
| otp\_code | query | Code from Google Authenticator | No | string |

‌

**Responses**

| Code | Description |
| :--- | :--- |
| 204 | Current user was blocked |

‌

**PUT**‌

**Description**‌

Updates current user data field‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| data | formData | Any additional key: value pairs in json string format | Yes | string |

‌

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Updates current user data field | API\_V2\_Entities\_UserWithFullInfo |

‌

**GET**‌

**Description**‌

Returns current user‌

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Returns current user | API\_V2\_Entities\_UserWithFullInfo |

‌

#### /api/v2/auth/resource/addresses <a id="api-v2-barong-resource-addresses"></a>

‌

**POST**‌

**Description**‌

Upload a new address approval document for current user‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| country | formData | Document type | Yes | string |
| address | formData | Document number | Yes | string |
| upload | formData | Array of Rack::Multipart::UploadedFile | Yes | string |
| city | formData | Document expiration date | Yes | string |
| postcode | formData | Any additional key: value pairs in json string format | Yes | string |

‌

**Responses**

| Code | Description |
| :--- | :--- |
| 201 | New address approval document was uploaded |
| 400 | Required params are empty |
| 401 | Invalid bearer token |
| 422 | Validation errors |

‌

#### /api/v2/auth/public/configs/auth0 <a id="api-v2-barong-public-configs-auth0"></a>

‌

**GET**‌

**Description**‌

Get auth0 configuration‌

**Responses**

| Code | Description |
| :--- | :--- |
| 200 | Get auth0 configuration |

‌

#### /api/v2/auth/public/configs <a id="api-v2-barong-public-configs"></a>

‌

**GET**‌

**Description**‌

Get auth configurations‌

**Responses**

| Code | Description |
| :--- | :--- |
| 200 | Get auth configurations |

‌

#### /api/v2/auth/public/version <a id="api-v2-barong-public-version"></a>

‌

**GET**‌

**Description**‌

Get auth version‌

**Responses**

| Code | Description |
| :--- | :--- |
| 200 | Get auth version |

‌

#### /api/v2/auth/public/time <a id="api-v2-barong-public-time"></a>

‌

**GET**‌

**Description**‌

Get server current unix timestamp.‌

**Responses**

| Code | Description |
| :--- | :--- |
| 200 | Get server current unix timestamp. |

‌

#### /api/v2/auth/public/ping <a id="api-v2-barong-public-ping"></a>

‌

**GET**‌

**Description**‌

Test connectivity‌

**Responses**

| Code | Description |
| :--- | :--- |
| 200 | Test connectivity |

‌

#### /api/v2/auth/public/password/validate <a id="api-v2-barong-public-password-validate"></a>

‌

**POST**‌

**Description**‌

Password strength testing‌

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| password | formData | User password | Yes | string |

‌

**Responses**

| Code | Description |
| :--- | :--- |
| 201 | Password strength testing |

‌

#### /api/v2/auth/public/kyc <a id="api-v2-barong-public-kyc"></a>

‌

**POST**‌

**Description**‌

KYC callback‌

**Responses**

| Code | Description |
| :--- | :--- |
| 201 | KYC callback |

‌

#### Models <a id="models"></a>

‌

**API\_V2\_Entities\_UserWithFullInfo**‌

Returns current user

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| email | string | User Email | No |
| uid | string | User UID | No |
| role | string | User role | No |
| level | integer | User level | No |
| otp | boolean | is 2FA enabled for account | No |
| state | string | User state: active, pending, inactive | No |
| referral\_uid | string | UID of referrer | No |
| data | string | Additional phone and profile info | No |
| csrf\_token | string | Сsrf protection token | No |
| username | string | User username | No |
| labels | API\_V2\_Entities\_Label | ​Content | No |
| phones | API\_V2\_Entities\_Phone | ​Content | No |
| profiles | API\_V2\_Entities\_Profile | ​Content | No |
| data\_storages | API\_V2\_Entities\_DataStorage | ​Content | No |
| created\_at | string | ​Content | No |
| updated\_at | string | ​Content | No |

‌

**API\_V2\_Entities\_Label**‌

List all labels for current user.

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| key | string | Label key. \[a-z0-9\_-\]+ should be used. Min - 3, max - 255 characters. | No |
| value | string | Label value. \[A-Za-z0-9\_-\] should be used. Min - 3, max - 255 characters. | No |
| scope | string | Label scope: 'public' or 'private' | No |
| created\_at | string | ​Content | No |
| updated\_at | string | ​Content | No |

‌

**API\_V2\_Entities\_Phone**‌

Returns list of user's phones

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| country | string | Phone country | No |
| number | string | Submasked phone number | No |
| validated\_at | s \(g\) | Phone validation date | No |

‌

**API\_V2\_Entities\_Profile**‌

Return profiles of current resource owner

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| first\_name | string | First Name | No |
| last\_name | string | Submasked last name | No |
| dob | date | Submasked birth date | No |
| address | string | Address | No |
| postcode | string | Address Postcode | No |
| city | string | City name | No |
| country | string | Country name | No |
| state | string | Profile state: drafted, submitted, verified, rejected | No |
| metadata | object | Profile additional fields | No |
| created\_at | string | ​Content | No |
| updated\_at | string | ​Content | No |

‌

**API\_V2\_Entities\_DataStorage**

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| title | string | Any additional data title | No |
| data | string | Any additional data json key:value pairs | No |
| created\_at | string | ​Content | No |
| updated\_at | string | ​Content | No |

‌

**API\_V2\_Entities\_APIKey**‌

Create an api key

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| kid | string | JWT public key | No |
| algorithm | string | Cryptographic hash function type | No |
| scope | string | Serialized array of scopes | No |
| state | string | active/non-active state of key | No |
| secret | string | Api key secret | No |
| created\_at | string | ​Content | No |
| updated\_at | string | ​Content | No |

‌

**API\_V2\_Entities\_Document**‌

Return current user documents list

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| upload | string | File url | No |
| doc\_type | string | Document type: passport, driver license, utility bill, identity card, institutional, address, residental | No |
| doc\_number | string | Submasked document number: AB123123 type | No |
| doc\_expire | string | Expire date of uploaded documents | No |
| metadata | string | Any additional stored data | No |
| created\_at | string | ​Content | No |
| updated\_at | string | ​Content | No |

‌

**API\_V2\_Entities\_Activity**‌

Returns user activity

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | integer | Activity ID | No |
| user\_ip | string | User IP | No |
| user\_ip\_country | string | User IP country | No |
| user\_agent | string | User Browser Agent | No |
| topic | string | Defined topic \(session, adjustments\) or general by default | No |
| action | string | API action: POST =&gt; 'create', PUT =&gt; 'update', GET =&gt; 'read', DELETE =&gt; 'delete', PATCH =&gt; 'update' or system if there is no match of HTTP method | No |
| result | string | Status of API response: succeed, failed, denied | No |
| data | string | Parameters which was sent to specific API endpoint | No |
| created\_at | string | ​Content | No |

‌

**API\_V2\_Entities\_Level**

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | integer | Level identifier, level number | No |
| key | string | Label key. \[A-Za-z0-9\_-\] should be used. Min - 3, max - 255 characters. | No |
| value | string | Label value. \[A-Za-z0-9\_-\] should be used. Min - 3, max - 255 characters. | No |

‌

**API\_V2\_Entities\_User**

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| email | string | User Email | No |
| uid | string | User UID | No |
| role | string | User role | No |
| level | integer | User level | No |
| otp | boolean | is 2FA enabled for account | No |
| state | string | User state: active, pending, inactive | No |
| referral\_uid | string | UID of referrer | No |
| data | string | Additional phone and profile info | No |
| username | string | User username | No |

‌

**API\_V2\_Entities\_UserWithProfile**

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| email | string | User Email | No |
| uid | string | User UID | No |
| role | string | User role | No |
| level | integer | User level | No |
| otp | boolean | is 2FA enabled for account | No |
| state | string | User state: active, pending, inactive | No |
| referral\_uid | string | UID of referrer | No |
| data | string | Additional phone and profile info | No |
| username | string | User username | No |
| profiles | API\_V2\_Entities\_Profile | ​Content | No |
| created\_at | string | ​Content | No |
| updated\_at | string | ​Content | No |

‌

**API\_V2\_Entities\_UserWithKYC**

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| email | string | User Email | No |
| uid | string | User UID | No |
| role | string | User role | No |
| level | integer | User level | No |
| otp | boolean | is 2FA enabled for account | No |
| state | string | User state: active, pending, inactive | No |
| referral\_uid | string | UID of referrer | No |
| data | string | Additional phone and profile info | No |
| username | string | User username | No |
| profiles | API\_V2\_Entities\_Profile | ​Content | No |
| labels | API\_V2\_Entities\_AdminLabelView | ​Content | No |
| phones | API\_V2\_Entities\_Phone | ​Content | No |
| documents | API\_V2\_Entities\_Document | ​Content | No |
| data\_storages | API\_V2\_Entities\_DataStorage | ​Content | No |
| comments | API\_V2\_Entities\_Comment | ​Content | No |
| created\_at | string | ​Content | No |
| updated\_at | string | ​Content | No |

‌

**API\_V2\_Entities\_AdminLabelView**

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| key | string | Label key. \[a-z0-9\_-\]+ should be used. Min - 3, max - 255 characters. | No |
| value | string | Label value. \[A-Za-z0-9\_-\] should be used. Min - 3, max - 255 characters. | No |
| scope | string | Label scope: 'public' or 'private' | No |
| description | string | Label desc: json string with any additional information | No |
| created\_at | string | ​Content | No |
| updated\_at | string | ​Content | No |

‌

**API\_V2\_Entities\_Comment**

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | integer | Comment id | No |
| author\_uid | string | Comment author UID | No |
| title | string | Comment title | No |
| data | string | Comment plain text | No |
| created\_at | string | ​Content | No |
| updated\_at | string | ​Content | No |

‌

**API\_V2\_Entities\_ServiceAccounts**

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| email | string | User Email | No |
| uid | string | User UID | No |
| role | string | Service Account Role | No |
| level | integer | User Level | No |
| state | string | Service Account State: active, disabled | No |
| user | API\_V2\_Entities\_User | ​Content | No |
| created\_at | string | ​Content | No |
| updated\_at | string | ​Content | No |

​

