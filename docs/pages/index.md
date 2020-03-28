---
title: Getting Started
subtitle: A guide to creating your first Battlesnake
permalink: /
layout: page
---

## What is Battlesnake?

A Battlesnake is a programmed web server that implements the [Battlesnake API](/snake-api) to play the game snake against other Battlesnakes. When a game is running, the Battlesnake Game Engine will make HTTP requests to your server, sending you game information and asking for your next move.

## Step 1: Build Your Battlesnake

Select a technology you want to use to program your Battlesnake server. Anything that can process a web request and be deployed to the internet will work. There are several well documented [Starter Snakes Projects](/stater-snakes) that can be used as a base if you don't want to start from scratch. Each is built with a popular programming language and web application framework.

A functional Battlesnake server must support 4 endpoints that will be called at different times during each Battlesnake game.

#### [GET /start](/snake-api#tag/endpoints/paths/~1start/post)
The engine is asking your Battlesnake if it is alive and functional.

#### [POST /start](/snake-api#tag/endpoints/paths/~1ping/post)
Notifies your Battlesnake that it is participating in a new game.

#### [POST /move](/snake-api#tag/endpoints/paths/~1move/post)
Called once per turn of each game, providing important information about the game board and asking your Battlesnake for its next move.

#### [POST /end](/snake-api#tag/endpoints/paths/~1end/post)
Notifies your Battlesnake that the game is now over and which Battlesnake has won.

Each endpoint will be sent a JSON data blob by the Game Engine and your server must respond with a HTTP 200 OK status code and an appropriate JSON response. The protocol for these requests and responses are defined in detail in the [Battlesnake API Reference](/snake-api).

<div class="alert alert-secondary alert-outline">
<h5 class="text-secondary"><strong> <svg class="float-left m-r-10" viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg" width="20" height="20" style="fill:#32C1DB"><circle fill="none" cx="13" cy="29" r="9" /><path d="M88 57l11-11a3 3 0 0 0-4-5L82 54H43l48-38V0H0v100h89L44 60h38l13 13a3 3 0 0 0 4-5zM13 38a9 9 0 1 1 10-9 9 9 0 0 1-10 9z" /></svg> Battlesnake Wisdom - Concurrent Games </strong></h5>
<p class="text-secondary">Your Battlesnake is a live web service and could be playing multiple games at the same time. The <strong>/start</strong>, <strong>/move</strong> and <strong>/end</strong> requests will all contain a Game ID that uniquely identifies which game the request is for. You should develop your snake to handle requests from different games at the same time.</p>
</div>

## Step 2: Deploy Your Battlesnake

Before your Battlesnake can enter games and do battle, it must be deployed to a publicly accessible web server. This can be done using a cloud hosting provider such as [Heroku](https://www.heroku.com/) or [Amazon Web Services](https://aws.amazon.com). Many of these services provide a free tier for new accounts.

Most of the [Starter Snake Projects](/starter-snakes) have instructions for deploying quickly to Heroku, which is a great option if you're new to web development or uncomfortable deploying code to a live server on your own.

<div class="alert alert-secondary alert-outline">
<h5 class="text-secondary"><strong> <svg class="float-left m-r-10" viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg" width="20" height="20" style="fill:#32C1DB"><circle fill="none" cx="13" cy="29" r="9" /><path d="M88 57l11-11a3 3 0 0 0-4-5L82 54H43l48-38V0H0v100h89L44 60h38l13 13a3 3 0 0 0 4-5zM13 38a9 9 0 1 1 10-9 9 9 0 0 1-10 9z" /></svg> Battlesnake Wisdom - Don't Take Too Long </strong></h5>
<p class="text-secondary">The Game Engine gives snakes 500 ms to respond to a <strong>/move</strong> request, including any network time. If your snake does not respond in time, the engine will reuse the move from the previous turn.</p>
</div>

## Step 3: Register Your Battlesnake

Once your Battlesnake is operational, it needs to be registered on the Battlesnake website. Click on the button below to setup a new snake.

[Click here to Register a new Battlesnake.](https://play.battlesnake.com/account/snakes/create/)

<div class="alert alert-secondary alert-outline">
<h5 class="text-secondary"><strong> <svg class="float-left m-r-10" viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg" width="20" height="20" style="fill:#32C1DB"><circle fill="none" cx="13" cy="29" r="9" /><path d="M88 57l11-11a3 3 0 0 0-4-5L82 54H43l48-38V0H0v100h89L44 60h38l13 13a3 3 0 0 0 4-5zM13 38a9 9 0 1 1 10-9 9 9 0 0 1-10 9z" /></svg> Battlesnake Wisdom - Names Are Important!</strong></h5>
<p class="text-secondary">Be creative with your Battlesnake name and description! Names like <em>test</em> or <em>snake1</em> are easy to confuse with other developer's Battlesnakes and fail to tell viewers anything about your Battlesnake.</p>

<p class="text-secondary">That said, creativity has limits. Make sure not to violate the <a href="https://play.battlesnake.com/about/conduct/">Battlesnake Code of Conduct</a> with your choices or your Battlesnake may be removed.</p>
</div>

## Step 4: Test Your Battlesnake

You are now ready to test your snake against others in live games. Creating new Battlesnakes games is super easy, here are some steps to get you started:

* Go to your Battlesnake's profile page on the Battlesnake website
* Click on the **Play Game** button - You will see a game creation form with your Battlesnake preselected.
* Use the **Add a Random Snake** button to add a challenger.
* Click on **Start Game** button to start the game!

You will be rewarded with a view of the board that includes your Battlesnake and whichever random challenger you were paired up with. Click on the Play button at the bottom of the board to start the match and see who wins!
