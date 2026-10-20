# Installation

## Single server

1. Put `ModernAuth-<version>.jar` in `plugins/`.
2. Start the server. `plugins/ModernAuth/` is created with `config.yml` and `messages.yml`.
3. Make sure `online-mode=false` in `server.properties`.

Accounts are stored in `plugins/ModernAuth/accounts.db` (SQLite), so there is nothing else to set up.

{% hint style="warning" %}
On a single server, `/premium` marks the account but the player still uses `/login`. Skipping `/login` needs BungeeCord or Velocity, see [BungeeCord and Velocity](proxy.md).
{% endhint %}

## With BungeeCord or Velocity

1. Put the same jar in the proxy's `plugins/` folder and in every backend server's `plugins/` folder.
2. Use **MySQL** on all of them, with the same database and table.
3. On every backend server set `proxy.enabled: true`.

The full setup is on [BungeeCord and Velocity](proxy.md).

{% hint style="warning" %}
When you update, **delete the old jar** before starting the server. Two versions in `plugins/` will both try to load.
{% endhint %}

## MySQL

In `plugins/ModernAuth/config.yml` on each backend server:

```yaml
database:
  type: mysql
  mysql:
    host: localhost
    port: 3306
    database: mineclusive
    username: root
    password: "your-password"
    pool-size: 10
  table: auth_accounts
```

The database must exist; the table is created for you.
