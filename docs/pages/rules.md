---
title: Battlesnake Game Rules
subtitle: Last Updated March 2020
permalink: /rules
layout: page
---

## What is Battlesnake?

Battlesnake is an autonomous survival game where your Battlesnake competes with others to find and eat food without being eliminated. To accomplish this, you will have to teach your Battlesnake to navigate the serpentine paths created by walls, other Battlesnakes, and your own growing tail without running out of health.

#### Winning the Game

Winning is quite simple: be the last Battlesnake left slithering. But slithering takes **health** and **space** &mdash; if you run out of either, you’ll be eliminated.

## Health

At the start of the game, your Battlesnake will be placed on the battlefield along with their opponents and everyone will have a full health meter. Every turn, your Battlesnake will be asked by the game engine to choose their next move: _up_, _down_, _left_, or _right_. After responding, your Battlesnake will move in the chosen direction. But slithering is hard work, and moving will drain your Battlesnake of one health for every square moved.

In order to restore that health your Battlesnake needs to find and eat the traditional food of Battlesnakes: brightly colored circular nutrition discs. If your Battlesnake enters the same square as a nutrition disc, they will immediately consume it, filling their health to maximum and increasing their length by one – one of many good reasons not to follow other Battlesnakes too closely (the view from there’s not great either).

#### Consuming Food

To eat a piece of food, your Battlesnake must move into the space that contains the food, this includes losing one health and fending off any other Battlesnakes that want to move into that space as well. Consuming food costs no health, so a Battlesnake can eat when at 0 health and be rejuvenated in time to keep moving.

<small>*the [algorithm](https://github.com/BattlesnakeOfficial/rules) is neither secret nor proprietary, but it is arguably super<small>

## Space

Battlesnakes need more than just food to survive, they need space to roam and be free. However, in Battlesnake, space is limited. Every turn, your Battlesnake has to move into a new space, but so do all other Battlesnakes. As the game goes on and all Battlesnakes consume food to stay alive, finding the best path through the remaining spaces gets more challenging.

#### Game Board

Battlesnake is played on a rectangular board of variable size, with up to 8 Battlesnakes competing at once in the same game. At the beginning of the game there will be food spread around the board, and on each subsequent turn additional food may be added to the board (according to a Super Secret Proprietary Algorithm*). It's also possible for multiple pieces of food to appear in any single turn.

Most importantly, the Battlesnake arena is also surrounded by walls &mdash; any Battlesnake attempting to sneak over one of these walls will be eliminated.

#### Body Collisions

Battlesnake is a battle of wits and honor. If your Battlesnake attempts to eat another Battlesnake's body, including its own, it will be eliminated for unsports-snake-like conduct.

#### Head-to-Head Collisions

When two Battlesnakes meet head-to-head, the outcome is a little more complext: the larger Battlesnake sticks around, and the smaller one is eliminated. If both Battlesnakes happen to be the same size, then both are eliminated.


#### Starting State

At the beginning of each game, every Battlesnake will be the same size and occupy a single space. This is very uncomfortable for Battlesnakes, and as they make their first few moves they will stretch out to be their full length.

## Programming Your Battlesnake

Battlesnake is more than a game of snakes and nutritious floating disc orbs, it’s also about people and how well they program those snakes. So it’s useful to understand exactly what happens during each turn. Each turn in a Battlesnake game is divided into 3 phases:

#### 1 - The Battlesnake engine sends identical board information to every Battlesnake.

The game engine server will send to each Battlesnake, in parallel, a /move request with information about the current state of the game board. This information includes the location of every piece of food on the board as well as the health of all Battlesnakes and the spaces they occupy. There is also some meta information about the game, like an id, turn #, and board dimensions for those Bobby Fischer Battlesnakes playing multiple games at once.

#### 2 - Each Battlesnake responds with their move.

After receiving information about the board, each Battlesnake has to respond with a move of "up", "down", "left", or "right" within the allowed timeout. You can find more specific details on what this response should look like in the [Official Battlesnake API](https://docs.battlesnake.com/snake-api). If your Battlesnake’s cybernetic brain fails to provide a valid response in time, instinct kicks in and they will continue moving in the same direction as the previous turn (on the first turn, this defaults to up) even if it means certain doom.

#### 3 - Move are resolved and a new board state is created.

At the end of the timeout period (or as soon as all Battlesnakes have responded with their move), the Battlesnake engine will resolve all moves and update the board state accordingly. This happens in a very specific order:

1. Each Battlesnake will have their health reduced by one.
2. Each Battlesnake will have a new body part added to the board in the next space in their chosen direction. This will be their new head.
3. Each Battlesnake will have their last body part (their tail) removed from the board.
4. Any Battlesnake that's found a nutrition disc gets to eat:
  * Their health reset to maximum.
  * They receive an additional body part placed on top of their current tail. This will extend their visible length by one on the next turn.
  * The food they ate is removed from the board.
5. Any Battlesnake that has run into a wall, another Battlesnake, or itself will be eliminated and removed from the board. They will have their status updated and will be notified with an /end request (no response necessary).
6. Potentially a new piece of food will be placed on the board, according to game parameters and food spawn algorithm.
7. If there are at least two Battlesnake still slithering, proceed to the next turn. Otherwise inform the remaining Battlesnake of its victory with an /end request and end the game.

#### Open Source Game Logic

Implementation of the Battlesnake Game Rules is open source, available at [github.com/BattlesnakeOfficial/rules](https://github.com/BattlesnakeOfficial/rules). We encourage all Battlesnake developers to review the rules code base and make any suggestions for new game modes and logic changes.

## Next Steps

To get started programming your Battlesnake, check out the available [Starter Snake Projects](/starter-snakes) to find specific guides for popular languages and technologies.

Don't forget to create an account at [play.battlesnake.com](https://play.battlesnake.com) to register your Battlesnake and start playing games.
