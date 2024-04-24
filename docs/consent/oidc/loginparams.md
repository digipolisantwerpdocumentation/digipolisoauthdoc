# Start login
[1. in schema](/consent/oidc/schema)

### Parameters

* [Auth methods](#Auth-methods)
* [Auth Type](#Auth-type)
* [Service](#Service)
* [Clientid](#Clientid)
* [Prompt](#Prompt)
* [Language](#Language)
* [Minimal assurance level](#Minimal-assurance-level)
* [Redirect uri](#Redirect-uri)
* [Save consent](#Save-consent)
* [Scope](#Scope)
* [State](#State)
* [login_hint](#login_hint)
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


### Prompt (beta)

?> Force Reauthentication in OIDC
**Known issue: By the login loop this might result in double login prompt**

| key          | Location | Required | Name         | values                     |
| ------------ | -------- |--------- | ------------ | -------------------------- |
| prompt       | query    | false    | prompt       | login                      |

```bash
# Example
/?prompt=login
```

### Max age (beta)

?> Maximum Authentication Age.
https://auth0.com/docs/authenticate/login/max-age-reauthentication#max_age-authentication-request-parameterhttps://auth0.com/docs/authenticate/login/max-age-reauthentication#max_age-authentication-request-parameter

| key          | Location | Required | Name         | values                     |
| ------------ | -------- |--------- | ------------ | -------------------------- |
| max_age      | query    | false    | max_age      | {integer}                  |

```bash
# Example
/?max_age=7200
```

### Save Consent

?> Save consent in stap [4.](/consent/oidc/schema) . Hiermee wordt de consent vraag niet meer opnieuw gesteld

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

?> Client id van workplace / keycloak client.

| key       | Location | Required | Name        | values       |
| --------- | -------- |--------- | ----------- | ------------ |
| client_id | query    | true     | clientid    | [CLIENTID]   |

```bash
# Example
/?client_id=[CLIENTID]
```

### Scope

?> scopes from keycloak client.

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
| auth_methods  | query    | true     | auth_method | space separated auth methods |

!> Enkel in Authentication2.0/3.0

```bash
# Example
/?auth_methods=fas-citizen-bmid%2Cfas-citizen-eid%2Cfas-citizen-totp%2Cfas-citizen-otp%2Ciam-aprofiel-userpass
```


### Minimal assurance level

?> Filter Auth methodes. Houd rekening met met auth_methods

| key                      | Location | Required | Name        | values                   |
| ------------------------ | -------- |--------- | ----------- | ------------------------ |
| minimal_assurance_level  | query    | false    | scope       | low / substantial / high |

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

### Code Challenge

?> oidc+pkce concept

| key            | Location | Required   | Name        | values               |
| -------------- | -------- |----------- | ----------- | -------------------- |
| code_challenge | query    | for mobile | Language    | hashed code_verifier |

```bash
# Example
/?code_challenge=abc
```
### Nonce

?> oidc concept check nonce in token after exchange

| key            | Location | Required   | Name        | values               |
| -------------- | -------- |----------- | ----------- | -------------------- |
| nonce          | query    | false      | Language    | nonce                |

```bash
# Example
/?nonce=nonceabc
```
### OIDC issuer

?> oidc_issuer

| key            | Location | Required   | Name        | values               |
| -------------- | -------- |----------- | ----------- | -------------------- |
| oidc_issuer    | query    | true       | oidc_issuer | consentappurl        |

```bash
# Example
/?oidc_issuer=consentappurl
```
### login_hint

?> login_hint meegeven dit wordt in de username ingevuld

| key           | Location | Required | Name        | values       |
| ------------- | -------- |--------- | ----------- | ------------ |
| login_hint    | query    | false    | login_hint  | true / false |

```bash
# Example
/?login_hint=some_username
```
### redirect_uri_lng

?> Taal teruggeven in redirect

| key              | Location | Required | Name                 | values       |
| ---------------- | -------- |--------- | -------------------- | ------------ |
| redirect_uri_lng | query    | false    | redirect_uri_lng     | true / false |

```bash
# Example
/?redirect_uri_lng=true
```
### redirect_uri_ssokey

?> ssoKey teruggeven in redirect

| key                   | Location | Required | Name                    | values       |
| --------------------- | -------- |--------- | ----------------------- | ------------ |
| redirect_uri_ssokey   | query    | false    | redirect_uri_ssokey     | true / false |

```bash
# Example
/?redirect_uri_ssokey=true
```
