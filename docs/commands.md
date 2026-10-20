# Commands

| Command | Alias | Who | What it does |
| --- | --- | --- | --- |
| `/register <password> <confirm password>` | `/reg` | New players | Creates the account and logs in |
| `/login <password>` | `/l` | Registered players | Logs in |
| `/premium` | | Logged-in players | Shows a warning and asks for `/premium confirm` |
| `/premium confirm` | | Logged-in players | Checks the name with Mojang and makes the account premium (within 30 seconds of `/premium`) |

## Passwords

* Between `auth.password.min-length` and `auth.password.max-length` characters (6 to 64 by default).
* Can't be the same as the player's name.
* Both passwords in `/register` must match.

## Before logging in

Only `/login`, `/l`, `/register` and `/reg` work. Change the list with `auth.allowed-commands` in [Config](config.md).
