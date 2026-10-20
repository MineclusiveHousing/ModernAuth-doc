# ModernAuth

Login and register for offline-mode servers, with premium (Mojang) accounts that skip `/login` and Bedrock players that log in through Xbox.

**Current version: 0.2.0**

## Compatibility

| Requirement | Version |
| --- | --- |
| Server | Spigot **1.21.11** (tested). It only uses the Bukkit API, so Paper 1.21 should work too. |
| Proxy | **BungeeCord** or **Velocity** (optional, needed for premium auto-login) |
| Java | **21** or newer |
| Database | **SQLite** (default, nothing to set up) or **MySQL** (needed with a proxy) |
| Optional | **Geyser + Floodgate** for Bedrock players |

One jar runs on Spigot, BungeeCord and Velocity.

## Features

* **Register and login**: `/register <password> <confirm password>` and `/login <password>`.
* **Locked until logged in**: players can't move, chat, use other commands, open inventories, break or place blocks, or take damage before they log in.
* **Timeout and attempts**: players are kicked when they take too long or type the wrong password too many times.
* **Premium accounts**: `/premium` links the account to its Mojang account. Through BungeeCord or Velocity the player then logs in through Mojang and skips `/login`.
* **Keeps player data**: premium players keep the UUID they had before `/premium`, so inventories and other plugin data stay.
* **Bedrock support**: Geyser + Floodgate players are logged in with their Xbox account and get an account on their first join.
* **Safe passwords**: passwords are stored as PBKDF2-HMAC-SHA256 hashes, and `/login` and `/register` never show in the console log.
* **No lag**: every database call and password check runs off the main thread.
* **Configurable**: every message is in `messages.yml`.
