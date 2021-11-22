# Start login
[1. in schema](/consent/schema)

### Parameters

* [Auth methods](#Auth-methods)
* [Auth Type](#Auth-type)
* [Service](#Service)
* [Clientid](#Clientid)
* [Language](#Language)
* [Minimal assurance level](#Minimal-assurance-level)
* [Redirect uri](#Redirect-uri)
* [Save consent](#Save-consent)
* [Scope](#Scope)
* [State](#State)


### State

?> Security measure.

| key   | Location | Required | Name         | values       |
| ------| -------- |--------- | ------------ | ------------ |
| state | query    | false    | state        | random value |

!> Check if the value matches on return

```bash
# Example
/?state=32132465464
```

### Response type

?> Return token or Code.

| key           | Location | Required | Name          | values                   |
| ------------- | -------- |--------- | ------------- | ------------------------ |
| response_type | query    | true     | response type | code / token(deprecated) |

!> Token is deprecated for Security reasons

```bash
# Example
/?response_type=code
```


### Save Consent

?> Save consent in step [4.](/consent/schema) This prevents the consent from being asked every time to the same user.

| key          | Location | Required | Name         | values                     |
| ------------ | -------- |--------- | ------------ | -------------------------- |
| save_consent | query    | false    | save consent | true / false (default false) |

```bash
# Example
/?save_consent=true
```


### Redirect uri

?> Url where code should be send to.

| key          | Location | Required | Name         | values                     |
| ------------ | -------- |--------- | ------------ | -------------------------- |
| redirect_uri | query    | true     | Redirect uri | [APPURL_TO_SEND_CODE_TO]   |

!> Note that this url should also be set in the api-store

```bash
# Example
/?redirect_uri=http://localhost/auth/login/
```


### Clientid

?> Client id from api-store / workplace.

| key       | Location | Required | Name        | values       |
| --------- | -------- |--------- | ----------- | ------------ |
| client_id | query    | true     | clientid    | [CLIENTID]   |

```bash
# Example
/?client_id=[CLIENTID]
```


### Auth methods

?> Allowed Auth methods. Order is respected

| key           | Location | Required | Name        | values                       |
| ------------- | -------- |--------- | ----------- | ---------------------------- |
| auth_methods  | query    | true     | scope       | space separated auth methods |

!> Only in Authentication2.0

```bash
# Example
/?auth_methods=fas-citizen-bmid%2Cfas-citizen-eid%2Cfas-citizen-totp%2Cfas-citizen-otp%2Ciam-aprofiel-userpass
```


### Minimal assurance level

?> Filter Auth methods. Combined with auth_methods

| key           | Location | Required | Name        | values                   |
| ------------- | -------- |--------- | ----------- | ------------------------ |
| save_consent  | query    | false    | scope       | low / substantial / high |

!> Only in Authentication2.0

```bash
# Example
/?minimal_assurance_level=low
```

### Language

?> UI language

| key | Location | Required | Name        | values            |
| --- | -------- |--------- | ----------- | ----------------- |
| lng | query    | false    | Language    | nl / fr / en / de |

```bash
# Example
/?lng=nl
```
