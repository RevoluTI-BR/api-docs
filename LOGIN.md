## Login

Request
```
POST /auth/login HTTP/1.1
Content-Type: application/json
Host: https://api.revoluti.com.br
```
Body
```json
{
  "username": "admin@revoluti.com.br",
  "password": "password"
}
```

Response
```json
{
  "access_token": "{TOKEN}", // armazenar
  "refresh_token": "{REFRESH_TOKEN}",
  "user": {
    "id": "bf71d272-f167-49ce-9d91-068df0c5ce4a",
    "username": "admin@revoluti.com.br",
    "type": "Master",
    "name": "ADMIN",
    "group": {
      "name": "Cliente"
    },
    "default_route": "audit"
  }
}
```