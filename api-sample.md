# Quick Start

#### Create files

Create a new directory for your project \(E.g. sample\_game\) and create following files in it:

* sample\_game
  * conso.json
* * index.html
  * controller.html
  * js
    * conso-1.0.0.js

The `conso.json` is for configuration of the game.

The `index.html` is for the gaming's screen.

The `controller.html` is for the players' screen



#### Javascript API file

Include the Javascript API file in both `index.html` and `controller.html`



#### Sample of getting user input

`index.html`

```
<!doctype html>
<html>

<head>
    <meta charset="utf-8">
    <title>Sample Screen HTML</title>
    <meta name="description" content="">
    <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1">
    <style>
        .container {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100vh;
            text-align: center;
            margin: 0 auto;
            padding: 0;
        }

        .container:before {
            content: '';
            display: inline-block;
            vertical-align: middle;
            height: 100%;
        }

        .wrapper {
            display: inline-block;
            vertical-align: middle;
            width: 80%;
            font-size: 80px;
        }
    </style>
</head>

<body>
    <div class="container">
        <div class="wrapper">
            <span>Player Click: </span>
            <span id="action"></span>
        </div>
    </div>
    <script type="text/javascript" src="js/conso-1.0.0.js"></script>
    <script>
        var webSocket;
        var wsConfig = {
            isDisplay: true,
            onConnect: function(event) {
                var players = webSocket.checkActivePlayer();
                players.forEach(x => {
                    webSocket.message(x.id, {
                        color: x.color
                    });
                })
            },
            onAllPlayersLoaded: function() {
                console.log('allPlayersLoaded');
            },
            onMessage: function(id, data) {
              document.getElementById('action').innerHTML = data.value;
            }
        }
        webSocket = new Conso(wsConfig);
    </script>
</body>

</html>
```



`controller.html`

```
<!doctype html>
<html>

<head>
    <meta charset="utf-8">
    <title>Sample Controller</title>
    <meta name="description" content="">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <style>
        @import url('https://fonts.googleapis.com/css?family=Work+Sans:400,700,900');
        @import url('https://fonts.googleapis.com/icon?family=Material+Icons');

        body {
            font-family: 'Work Sans', sans-serif;
            user-select: none;
            text-align: center;
        }

        h1 {
            font-size: 2em;
            font-weight: 800;
            white-space: pre;
            line-height: 0.85;
            color: #999;
        }

        .container {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100vh;
            text-align: center;
            margin: 0 auto;
            padding: 0;
        }

        .container:before {
            content: '';
            display: inline-block;
            vertical-align: middle;
            height: 100%;
        }

        .buttons {
            display: inline-block;
            vertical-align: middle;
            max-width: 30em;
            margin: 0 auto;
        }

        hr {
            margin: 0 0 1em;
            border: 0;
        }

        .axes-L {
            margin-right: 1.5em;
        }

        button {
            font-family: 'Work Sans', sans-serif;
            display: inline-block;
            border: 0;
            padding: 0;
            background: #BAB9B9;
            color: #6C7073;
            font-weight: 600;
            border-radius: 2em;
            width: 2em;
            height: 2em;
            font-size: 2em;
            outline: none;
            border-bottom: 0.15em solid rgba(0, 0, 0, 0.5);
        }

        button.active,
        button:active {
            border-bottom: 0.15em solid transparent;
            transform: scale(0.9);
        }


        .button-circle {
            color: #FFF;
        }

        .button-axes {
            background: #222;
            color: white;
        }

        .button-axes {
            width: 1.6em;
            height: 1.6em;
            line-height: 1.3;
            border-radius: 0.2em;
            color: #666;
        }


        .button-A {
            background: #ED1D29;
        }

        .button-B {
            background: #FFB930;
        }

        button .arrow {
            display: inline-block;
            width: 0;
            height: 0;
            vertical-align: middle;
            font-size: 0.35em;
            line-height: 0;
            border-color: rgba(0, 0, 0, 0.5);
            border: 0 solid transparent;
            color: inherit;
        }

        button .arrow-left {
            border-right-color: #999;
            border-right-width: 1em;
            border-bottom-width: 1em;
            border-top-width: 1em;
            margin-left: -0.25em;
        }

        button .arrow-right {
            border-left-color: #999;
            border-left-width: 1em;
            border-bottom-width: 1em;
            border-top-width: 1em;
            margin-right: -0.25em;
        }

        button .arrow-up {
            border-bottom-color: #999;
            border-bottom-width: 1em;
            border-left-width: 1em;
            border-right-width: 1em;
            margin-top: -0.25em;
        }

        button .arrow-down {
            border-top-color: #999;
            border-top-width: 1em;
            border-left-width: 1em;
            border-right-width: 1em;
            margin-bottom: -0.25em;
        }
    </style>
</head>

<body>
    <div class="container">
        <div class="buttons">
            <h1>Sample Controller</h1>
            <hr>
            <button class="button-circle button-A" value="A">A</button>
            <button class="button-circle button-B" value="B">B</button>
            <hr>
            <button class="button-axes axes-U" value="up">
              <i class="arrow arrow-up"></i>
            </button>
            <hr>
            <button class="button-axes axes-L" value="left">
              <i class="arrow arrow-left"></i>
            </button>
            <button class="button-axes axes-R" value="right">
              <i class="arrow arrow-right"></i>
            </button>
            <hr>
            <button class="button-axes axes-D" value="down">
              <i class="arrow arrow-down"></i>
            </button>
        </div>
    </div>

    <script type="text/javascript" src="js/conso-1.0.0.js"></script>
    <script>
        var wsConfig = {
            onMessage: function(id, data) {
                // Get color of the player
                var body = document.getElementsByTagName("body")[0];
                body.style.background = data.color;
            }
        }
        var webSocket = new Conso(wsConfig);

        Array.from(document.getElementsByTagName("button")).forEach(function(item) {
            item.addEventListener('touchstart', function() 
                webSocket.message('display',{value: this.value})
            }, false);
        });

    </script>
</body>

</html>
```

#### 

#### Test Your Game

![](/assets/螢幕快照 2017-04-14 下午3.17.34.png)



