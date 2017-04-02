# Category: Player
---

These methods and event handlers check players' connection status.


{% method %}

### .checkActivePlayer ()

Get the number of players connected to the local host server.

> .checkActivePlayer()

{% sample lang="js" %}

Here is how to get the players' list.

```js
var wsConfig = {
    onConnect: function (event) {
        var players = webSocket.checkActivePlayer();
    }
}
var webSocket = new Conso(wsConfig);
```

{% endmethod %}