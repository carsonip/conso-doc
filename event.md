# Category: Connectivity
---

These methods and event handlers handle message between server and clients.

### isDisplay

Indicates whether the client is a display client or a mobile client.

```js
var wsConfig = {
    isDisplay: true
}
var conso = new Conso(wsConfig);
```



{% method %}
### .onConnect()

Bind an event hander to the 'connect' of webSocket event.

> .onConnect( eventData )

__eventData__

Type: Anything

The object of the connection event.


{% sample lang="js" %}

Here is how to establish the safety connection between server and client.


```js
var wsConfig = {
    onConnect: function (event) {
        //call other api function
    }
}
var conso = new Conso(wsConfig);
```

{% endmethod %}


{% method %}
### .onClose()

Bind an event hander to the 'close' of webSocket event.

> .onClose( eventData )

__eventData__

Type: Anything

The object of the close event.


{% sample lang="js" %}

Here is how to close the connection between server and client.

```js
var wsConfig = {
    onClose: function (event) {
        //do something
    }
}
var conso = new Conso(wsConfig);
```

{% endmethod %}

{% method %}
### .onPlayerLoaded()
 Only received by display
WIP

{% endmethod %}

{% method %}
### .onAllPlayersLoaded()
both display and controller will receive
WIP

{% endmethod %}





