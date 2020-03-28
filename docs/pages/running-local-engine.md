---
title: Running a Local Engine
subtitle: Run Battlesnake games locally to test your code without deploying.
permalink: /run-local-engine
layout: page
---

## The Battlesnake Engine

The Battlesnake Engine is responsible for running games and sending requests to Battlesnake servers. Any time you use the [Create Game](https://play.battlesnake.com/account/games/create/) form on [play.battlesnake.com](play.battlesnake.com), you are communicating with the Battlesnake engine. We encourage everyone to use this publicly available engine for Battlesnake testing and debugging as it will always run the latest version of the code and will contain the rule sets used in public events and tournaments.

## Running the Engine Locally

Some developers prefer to run a local version of the engine to assist with debugging and development iteration. For this purpose we have provided some binary releases of the engine server that developers can setup. These binaries are from a older version of the engine, that provides the basic functionality for testing core Battlesnake behavior.

{% include wisdom.html
    title="Advanced Development Ahead!"
    content="
Running the Battlesnake engine locally is **not required or recommended** for most developers - especially those new to Battlesnake. Once you have a working Battlesnake and are comfortable running games, running the engine locally can be useful for advanced local testing and algorithm development." %}

#### Step 1: Download the Binary Release

Download the [0.2.25 Engine Release](https://github.com/battlesnakeio/engine/releases/tag/0.2.25) for your architecture to a folder somewhere on your machine.

Unpack/unzip the downloaded release. You should have an engine binary, the LICENSE, and the README available in the unpackaged folder

#### Step 2: Start the Engine

Open a terminal window and run the engine binary with `./engine dev` (on MacOS & Linux) or `engine dev` (on Windows). When the engine launches it should show output the following:

```
$ ./engine dev
INFO[0000] dev form available at http://localhost:3010/
INFO[0000] Battlesnake controller serving                listen=":3004"
INFO[0000] board available at http://localhost:3009/
INFO[0000] Battlesnake worker starting                   worker=9
INFO[0000] Battlesnake worker starting                   worker=0
INFO[0000] Battlesnake api serving                       listen=":3005"
INFO[0000] Battlesnake worker starting                   worker=1
INFO[0000] Battlesnake worker starting                   worker=2
INFO[0000] Battlesnake worker starting                   worker=3
INFO[0000] Battlesnake worker starting                   worker=4
INFO[0000] Battlesnake worker starting                   worker=5
INFO[0000] Battlesnake worker starting                   worker=6
INFO[0000] Battlesnake worker starting                   worker=7
INFO[0000] Battlesnake worker starting                   worker=8
INFO[0000] controller rpc                                duration="23.55µs" method=/pb.Controller/Ping
INFO[0000] connection to controller healthy              version=unreleased
```

#### Step 3: Create a Game

Running the engine in dev mode will launch a web server with a simple form for creating games.

In a browser, go to [localhost:3010](http://localhost:3010/). You should see a page that looks like the image below. The left side of the page is the form for creating a game. The right side of the page is the Battlenake board, which will render once a game is started.

To start a game, provide a `Name` and `URL` for each Battlesnake, then click on the **Start Game** button.

<div class="alert alert-secondary alert-outline">
<img src="/assets/images/engine-devmode-form.png" alt="create game form"/>
</div>

The game will be created on local engine server and start running. You should see requests reaching your Battlesnake server and within a few seconds the game will be rendered on the board. Click on the Play link at the bottom of the board to watch the game. In addition, use the **Add Snake** button to define up to 8 snakes for a game.
