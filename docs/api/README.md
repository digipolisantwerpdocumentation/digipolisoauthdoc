# API calls

#### Get User sessions
```GET {baseurl}/sessions/{ssoKey}```

| key       | Location | Required | Name         | values             |
| --------- | -------- |--------- | ------------ | ------------------ |
| ssoKey    | url      | true     | ssoKey       | value from cookie  |

example response
```javascript
{
  "sessions": [
    {
        "lastLogin": "2021-11-26T13:11:39.840Z",
        "authenticationMethod": "astad.mprofiel.v1",
        "name": "Jonn doe",
        "assuranceLevel": "low",
        "user": "ex123456"
    }
  ]
}
```

#### Get the browserSession for a specific app
```GET /sessions/{ssoKey}/clientids/{clientId}```

| key       | Location | Required | Name         | values             |
| --------- | -------- |--------- | ------------ | ------------------ |
| ssoKey    | url      | true     | ssoKey       | value from cookie  |
| clientId  | url      | true     | clientId     | client id of app   |

example response
```javascript
{
  "lastLogin": "2021-11-26T13:11:39.840Z",
  "authenticationMethod": "astad.mprofiel.v1",
  "name": "Jonn doe",
  "assuranceLevel": "low",
  "user": "ex123456"
}
```

#### Delete User sessions
```DELETE {baseurl}/sessions/{ssoKey}```

| key       | Location | Required | Name         | values             |
| --------- | -------- |--------- | ------------ | ------------------ |
| ssoKey    | url      | true     | ssoKey       | value from cookie  |


#### Delete the browserSession for a specific app
```DELETE /sessions/{ssoKey}/clientids/{clientId}```

| key       | Location | Required | Name         | values             |
| --------- | -------- |--------- | ------------ | ------------------ |
| ssoKey    | url      | true     | ssoKey       | value from cookie  |
| clientId  | url      | true     | clientId     | client id of app   |

