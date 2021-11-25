# Start Logout
[1. in schema](/consent/schema?id=logout-flow)

### Parameters

* [Clientid](#client_id)
* [service](#service)
* [data](#data)
* [auth_type](#auth_type)


### Clientid

?> Client id from api-store / workplace.

| key       | Location | Required | Name        | values       |
| --------- | -------- |--------- | ----------- | ------------ |
| client_id | query    | true     | clientid    | [CLIENTID]   |

```bash

# Example
/?client_id=[CLIENTID]
```

### Service

?> The service to log out, e.g. "astad.mprofiel.v1"


| key       | Location | Required | Name        | values             |
| --------- | -------- |--------- | ----------- | ------------------ |
| service   | query    | true     | service     | auth1.0 services   |

```bash

# Example
/?service=astad.mprofiel.v1
```

### Data

?> Additional parameters encrypted


##### DataObject

| key            | Location              | Required | Name         | values         |
| -------------- | --------------------- |--------- | ------------ | -------------- |
| user_id        | encrypted json object | true     | user_id      | [USER_ID]      |
| access_token   | encrypted json object | true     | access_token | [ACCESS_TOKEN] |
| redirect_uri   | encrypted json object | true     | redirect_uri | [ACCESS_TOKEN] |

```javascript
// javascript (nodejs)

const crypto = require('crypto');
const algorithm = 'aes-128-ctr';

const client_secret = 'supersecret_client_secret';

const data = JSON.stringify({
  user_id: 'dummy_user_id',
  access_token: 'dummy_user_access_token',
  redirect_uri: 'http://localhost:3000',
});


function encrypt(text, password) {
  const hash = crypto.createHash('sha1');
  hash.update(password);
  const key = hash.digest().slice(0, 16);
  const ivBuffer = Buffer.alloc(16);
  const cipher = crypto.createCipheriv(algorithm, key, ivBuffer);
  let crypted = cipher.update(text, 'utf8', 'hex');
  crypted += cipher.final('hex');
  return crypted;
}

const encrypted_data = encrypt(data, client_secret)
// bc8be81f167a6e90f1d4bc1e69b732324fdbe8cb6ad655066e1374bf037b397d70f48ef2a090fabd7bb696825459873824e392017698ec8861e4478a960204d6b43245d0633d8870a04be4c27ae7f83af1ee8ab9fbe21eade581f754629dba88a1620aff500313bd3deac4

```

```bash

# Example
/?data=bc8be81f167a6e90f1d4bc1e69b732324fdbe8cb6ad655066e1374bf037b397d70f48ef2a090fabd7bb696825459873824e392017698ec8861e4478a960204d6b43245d0633d8870a04be4c27ae7f83af1ee8ab9fbe21eade581f754629dba88a1620aff500313bd3deac4
```

### Auth type

?> optional: use the same auth_type which was passed to the login redirect (if set to "so", Azure logout for SO will be triggered)

| key       | Location | Required | Name        | values             |
| --------- | -------- |--------- | ----------- | ------------------ |
| auth_type | query    | false    | auth_type   | so                 |

```bash
# Example
/?auth_type=so
```
