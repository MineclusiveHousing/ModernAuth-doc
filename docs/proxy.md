# BungeeCord and Velocity

The same `ModernAuth-<version>.jar` runs on the proxy. On the proxy it only handles premium login; `/login` and `/register` stay on the backend servers.

## Setup

1. Put the jar in `plugins/` on the proxy and on every backend server.
2. Start the proxy once, then fill in MySQL in the proxy's `plugins/ModernAuth/config.yml`.
3. On every backend server, in `plugins/ModernAuth/config.yml`, set `database.type: mysql` with the same host, database and table as the proxy, and turn the proxy mode on:
   ```yaml
   proxy:
     enabled: true
   ```
4. Restart the proxy and the backend servers.

{% hint style="warning" %}
The proxy and every backend server must use the **same MySQL database and table**. SQLite can't be shared, so premium auto-login stays off with SQLite.
{% endhint %}

## Proxy settings

| Proxy | Setting |
| --- | --- |
| BungeeCord | `online_mode: false` and `ip_forward: true` in `config.yml` |
| Velocity | `online-mode = false` and a `player-info-forwarding-mode` (`modern` recommended) in `velocity.toml` |

Backend servers must only accept players through the proxy: `bungeecord: true` in `spigot.yml` for BungeeCord, or Velocity's forwarding secret set on the backend for modern forwarding. Otherwise players can skip the proxy and its premium check.

## UUIDs

| Proxy | With `keep-offline-uuid: true` |
| --- | --- |
| Velocity | Keeps the old UUID through Velocity's game profile event |
| BungeeCord | Keeps the old UUID. If a BungeeCord update stops this from working, the console warns and the player joins with their Mojang UUID |

## Check IP

With `proxy.check-ip: true` on the backend, the auto-login only happens when the player's IP matches the IP the proxy verified. Keep it on unless your forwarding hides real IPs.
