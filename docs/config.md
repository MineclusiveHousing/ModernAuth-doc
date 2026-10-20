# Config

## Server: `plugins/ModernAuth/config.yml`

```yaml
database:
  type: sqlite            # sqlite or mysql
  sqlite-file: accounts.db
  mysql:
    host: localhost
    port: 3306
    database: mineclusive
    username: root
    password: ""
    pool-size: 10
  table: auth_accounts

auth:
  login-timeout: 60       # seconds to /login or /register before a kick
  reminder-interval: 10   # seconds between "please log in" messages
  max-attempts: 3         # wrong passwords before a kick
  password:
    min-length: 6
    max-length: 64
  allowed-commands: [login, l, register, reg]

premium:
  lookup-url: "https://api.mojang.com/users/profiles/minecraft/%name%"

proxy:
  enabled: false          # true behind BungeeCord or Velocity (needs MySQL)
  check-ip: true          # auto-login only from the IP the proxy verified

bedrock:
  auto-login: true        # Floodgate players skip /login and /register
```

## Proxy: `plugins/ModernAuth/config.yml` on BungeeCord or Velocity

```yaml
database:
  mysql:
    host: localhost
    port: 3306
    database: mineclusive
    username: root
    password: ""
    pool-size: 5
  table: auth_accounts

keep-offline-uuid: true
```

Use the same database and table as the backend servers. See [BungeeCord and Velocity](proxy.md).

## Messages: `plugins/ModernAuth/messages.yml`

Every message players see. Colour codes use `&`. Placeholders such as `%left%`, `%min%`, `%max%` and `%name%` are filled in for you. Keys you delete fall back to the default text.
