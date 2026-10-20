# Bedrock players

Bedrock players join through **Geyser** and **Floodgate**, which already sign them in with their Xbox account.

With `bedrock.auto-login: true` (default):

* On their first join an account is created for them, without a password.
* On every join they are logged in straight away, with no `/login` or `/register`.

Install Floodgate on the server that runs ModernAuth, as Floodgate's own guide describes. ModernAuth finds it by itself.

{% hint style="info" %}
Keep Floodgate's username prefix (`.` by default). It stops a Bedrock name from matching a Java player's account.
{% endhint %}

Set `bedrock.auto-login: false` to make Bedrock players use `/register` and `/login` like everyone else.
