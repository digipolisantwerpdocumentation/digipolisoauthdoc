# Authorization-code flow
---

```mermaid
graph TD

profile{ profiledatasource }
client{ APP / Client / BFF }
consent{ Consent APP }
IDP{ Identity provider }
startnode(start)

startnode-->client
client-->|5. exchange code & get profile data|profile
client-->|1. start login|consent
consent-->|4. Consent given OK, return code|client
consent-->|2. login|IDP
IDP-->|3. login OK|consent

style client fill:#ffeb3b, stroke:#000
style consent fill:#ef5350, stroke:#000
style IDP fill:#aed581, stroke:#000
style profile fill:#03a9f4, stroke:#000
style startnode fill:#e0e0e0, stroke:#000

```

### Flow

1. Click login link and redirect to consent app
2. Redirect to IDP and enter authentication credentials
3. Login successful redirect back to consent app
4. Request consent if necessary
5. Sends code to /oauth/token endpoint along with the application's Client ID and Client Secret. This results in access token, Request userdata with /me call
