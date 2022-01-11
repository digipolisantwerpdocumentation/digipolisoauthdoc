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

1. klik login link en redirect naar consent app
2. redirect naar de IDP en login
3. login ok, redirect terug naar de consent app
4. consent vraag indien nodig
5. code naar /oauth/token endpoint met de Client ID en Client Secret. Dit resulteert in access token, Vraag userdata op met /me call


# logout flow
---

```mermaid
graph TD

client{ APP / Client / BFF }
consent{ Consent APP }
IDP{ Identity provider }
startnode(start)

startnode-->client
client-->|1. start logout|consent
consent-->|2. remove session from idp|IDP
IDP-->|3. remove all temp & session data|consent
consent-->|4. callback back to app|client

style client fill:#ffeb3b, stroke:#000
style consent fill:#ef5350, stroke:#000
style IDP fill:#aed581, stroke:#000
style startnode fill:#e0e0e0, stroke:#000

```

### Flow

1. klik logout link en redirect naar de consent app
2. redirect naar IDP
3. logout ok, redirect terug naar de consent app
4. data clear van tijdelijke bronnen en callback redirect naar app
5. app verwijderd local session
