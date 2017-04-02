# Category: Message
---

These methods handle sending message between server and clients.


{% method %}
### .onMessage()

Bind an event hander to the 'message' of webSocket event.

> .onMessage( sender , eventData )

__sender__

Type: String

A String of ID of the sneder.


__eventData__

Type: Anything

The content of the message.


{% sample lang="js" %}
Here is how to print a message to `stdout` using JavaScript.

```js
var wsConfig = {
    onMessage: function(sender_id, data) {
        //anything you may want to do
    }
}
var webSocket = new Conso(wsConfig);
```

{% common %}
Whatever language you are using, the result will be the same.

```bash
$ My first method
```
{% endmethod %}


{% method %}
### .message()

Send a message to a specific display client or player client.
>message( receiver, data )

__receiver__

Type: String

A String of ID of the target.

__data__

Type: Anything

The content of the message.


{% sample lang="js" %}
Here is how to send a message.

```js
var wsConfig = {
    onConnect: function (event) {
        webSocket.message($player_id, 'this is an example');
    }
}
var webSocket = new Conso(wsConfig);
```

{% endmethod %}
