# Premium accounts

Players who own Minecraft can link their account to Mojang with `/premium`. Behind BungeeCord or Velocity they then log in through Mojang and skip `/login`.

## How players use it

1. Join and `/login` (or `/register`) as usual.
2. Type `/premium`. A warning explains what happens next.
3. Type `/premium confirm` within 30 seconds.
4. ModernAuth checks the name with Mojang. If the name belongs to a Mojang account, the account becomes premium.
5. From the next join they are logged in automatically.

{% hint style="danger" %}
After `/premium`, that name can only join with the **premium launcher**. The proxy refuses a cracked launcher using that name. Only use `/premium` on a name you own.
{% endhint %}

## How it works

* The proxy reads the account. If it is premium, that player (only that player) must log in through Mojang, like on an online-mode server.
* If Mojang accepts the player, the proxy marks the account as verified in the database, with the player's IP.
* The backend server sees the verified premium account and logs the player in without `/login`.
* When the player leaves, or the proxy restarts, the mark is cleared.

## Player data

With `keep-offline-uuid: true` (default) the player keeps the UUID they had before `/premium`, so inventories, ranks and other plugin data stay. Set it to `false` to give premium players their Mojang UUID instead.

## Without a proxy

On a single server, `/premium` still marks the account, but players keep using `/login`. Without the proxy, ModernAuth can't check that a player really owns the Mojang account.

## Bedrock accounts

Bedrock players can't use `/premium`; they already log in through Xbox. See [Bedrock players](bedrock.md).
