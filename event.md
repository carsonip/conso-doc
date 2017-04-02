# Category: Connectivity
---

These methods and event handlers handle message between server and clients.


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
var webSocket = new Conso(wsConfig);
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
var webSocket = new Conso(wsConfig);
```

{% endmethod %}





