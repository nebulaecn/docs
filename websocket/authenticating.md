# Authenticating

### **WebSocket Authentication**

\*\*\*\*

#### /api/v2/auth/identity/sessions/auth0 <a id="api-v2-barong-identity-sessions-auth0"></a>

‌

**POST**‌

**Description**‌

Auth0 authentication by id\_token‌



Authentication happens on websocket message with following JSON structure.

```text
{
  "jwt": "Bearer <Token>"
}
```



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

\*\*\*\*

### **WebSocket Connection**

**Save link** 

\*\*\*\*

**!!! Ниже копия процесса авторизации из раздела вебсокет**

### Authentication <a id="subscribe-to-streams"></a>

Authentication happens on websocket message with following JSON structure.

```text
{
  "jwt": "Bearer <Token>"
}
```

If authentication was done, server will respond successfully

```text
{
  "success": {
    "message": "Authenticated."
  }
}
```

Otherwise server will return an error

```text
{
  "error": {
    "message": "Authentication failed."
  }
}
```

If authentication JWT token has invalid type, server return an error

```text
{
  "error": {
    "message": "Token type is not provided or invalid."
  }
}
```

If other error occurred during the message handling server throws an error

```text
{
  "error": {
    "message": "Error while handling message."
  }
}
```

**Note:** Websocket API supports authentication only Bearer type of JWT token.

**Example** of authentication message:

```text
{
  "jwt": "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiYWRtaW4iOnRydWV9.TJVA95OrM7E2cBab30RMHrHDcEfxjoYZgeFONFh7HgQ"
}
```

### Streams subscription <a id="subscribe-to-streams"></a>

\*\*\*\*

### \*\*\*\*

\*\*\*\*

\*\*\*\*

\*\*\*\*



