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
* [redirect_uri_lng](#redirect_uri_lng)
* [redirect_uri_ssokey](#redirect_uri_ssokey)


### State

?> Security.

| key   | Location | Required | Name         | values       |
| ------| -------- |--------- | ------------ | ------------ |
| state | query    | false    | state        | random value |

!> Vergelijk waarde na login

```bash
# Example
/?state=32132465464
```

### Response type

?> Krijg een token of code.

| key           | Location | Required | Name          | values                   |
| ------------- | -------- |--------- | ------------- | ------------------------ |
| response_type | query    | true     | response type | code / token(deprecated) |

!> Token is deprecated

```bash
# Example
/?response_type=code
```


### Save Consent

?> Save consent in stap [4.](/consent/schema) . Hiermee wordt de consent vraag niet meer opnieuw gesteld

| key          | Location | Required | Name         | values                     |
| ------------ | -------- |--------- | ------------ | -------------------------- |
| save_consent | query    | false    | save consent | true / false (default false) |

```bash
# Example
/?save_consent=true
```


### Redirect uri

?> Url waar de code op zal binnenkomen.

| key          | Location | Required | Name         | values                     |
| ------------ | -------- |--------- | ------------ | -------------------------- |
| redirect_uri | query    | true     | Redirect uri | [APPURL_TO_SEND_CODE_TO]   |

!> Deze url moet ook ingesteld worden op de api-store

```bash
# Example
/?redirect_uri=http://localhost/auth/login/
```


### Clientid

?> Client id van api-store / workplace.

| key       | Location | Required | Name        | values       |
| --------- | -------- |--------- | ----------- | ------------ |
| client_id | query    | true     | clientid    | [CLIENTID]   |

```bash
# Example
/?client_id=[CLIENTID]
```

### Scope

?> scopes from service.

| key       | Location | Required | Name        | values        |
| --------- | -------- |--------- | ----------- | ------------- |
| scope     | query    | true     | scope       | [clientscope] |

```bash
# Example
/?scope=[scopelist spaced]
```


### Auth methods

?> Auth methodes. Volgorde wordt gerespecteerd.

| key           | Location | Required | Name        | values                       |
| ------------- | -------- |--------- | ----------- | ---------------------------- |
| auth_methods  | query    | true     | auth methods| space separated auth methods |

!> Enkel in Authentication2.0

```bash
# Example
/?auth_methods=fas-citizen-bmid%2Cfas-citizen-eid%2Cfas-citizen-totp%2Cfas-citizen-otp%2Ciam-aprofiel-userpass
```


### Minimal assurance level

?> Filter Auth methodes. Houd rekening met met auth_methods

| key                      | Location | Required | Name                       | values                   |
| ------------------------ | -------- |--------- | -------------------------- | ------------------------ |
| minimal_assurance_level  | query    | false    | minimal assurance level    | low / substantial / high |

!> Enkel in Authentication2.0

```bash
# Example
/?minimal_assurance_level=low
```

### Language

?> UI taal

| key | Location | Required | Name        | values            |
| --- | -------- |--------- | ----------- | ----------------- |
| lng | query    | false    | Language    | nl / fr / en / de |

```bash
# Example
/?lng=nl
```
### redirect_uri_lng

?> Taal teruggeven in redirect

| key              | Location | Required | Name        | values       |
| ---------------- | -------- |--------- | ----------- | ------------ |
| redirect_uri_lng | query    | false    | Language    | true / false |

```bash
# Example
/?redirect_uri_lng=true
```
### redirect_uri_ssokey

?> ssoKey teruggeven in redirect

| key                   | Location | Required | Name        | values       |
| --------------------- | -------- |--------- | ----------- | ------------ |
| redirect_uri_ssokey   | query    | false    | Language    | true / false |

```bash
# Example
/?redirect_uri_ssokey=true
```
