---
title: Customizing Your Snake
subtitle: How to make your Battlesnake as unique as you!
permalink: /snake-customization
layout: page
---

## Controlling the Appearance of your Battlesnake

Your Battlesnake's appearance is decided in your response to the `/start`

Make your snake unique by assigning it a color, head, and tail in your response to the [Battlesnake API Start Request](/snake-api#tag/endpoints/paths/~1start/post). Your response can select a `headType` and `tailType` style, as well as choose a `color` for your Battlesnake.

#### Example Start Request Response

```
{
	"color": "#736CCB",
	"headType": "beluga",
	"tailType": "curled"
}
```

The above response will customize your Battlesnake to look like this:

<div class="row p-10">
	<svg class="align-self-center ml-3 mr-0 w-40" fill="#736CCB" style="transform:rotateY(180deg);" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100">
	    <path d="M23 48c2 12 2 26 4 26 0 0-2 0 0 0s1-19-1-28c-1-10-2-19-1-28S31 1 42 0c10-1 19 5 25 12 5 7 7 11 8 21l1 12c0 3-2 17-1 21 1 5 8 7 8 7 8 3 16-1 17 1 0 2-3 5-8 6-11 3-24 6-30-4-4-8-2-18-2-26-1-9-1-20-6-28-2-3-6-5-9-4s-2 4-2 6c0 20 9 42 2 61-4 8-11 16-21 15l-4-1-2-1c-3-2-6-2-9-2-4 1-5 4-9 4V0c17 2 22 38 23 48z"/>
	</svg>
	<svg class="align-self-center mr-0 w-40" fill="#736CCB" viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
	    <path d="M0 0h100v100H0z"/>
	</svg>
	<svg class="align-self-center w-40" fill="#736CCB" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100">
	  <path d="M0 100h56L32 88l-5-14 73 2-10-48L50 0H0zm23-61a9 9 0 1 1-10 10 9 9 0 0 1 10-10z"/>
	</svg>
</div>


## Assigning a Color

Specify the `color` for your snake using a HEX code, such a `#736CCB`. The value you provide must be 7 characters long and begin with `#`. If you do not specify a color, specify an invalid option, a random color will be assigned.

## Choosing a Head and Tail

Find your favorite head and tail combo from the options below and use the name in the parameters `headType` and `tailType`. Both of these values default to `regular` if not provided or not recognized.

**Note:** These heads and tails can be mixed and matched however you want. They're arranged here by themes just for convenience.

#### Standard Theme

These customizations were part of the very first Battlesnake event, and hold a special spot in all our hearts.

<div class="row">
	<div class="col">
		<p class="text-right"><strong>Tail Types</strong></p>
		{% include custom_snake_tail.html name='regular' %}
		{% include custom_snake_tail.html name='block-bum' %}
		{% include custom_snake_tail.html name='bolt' %}
		{% include custom_snake_tail.html name='curled' %}
		{% include custom_snake_tail.html name='fat-rattle' %}
		{% include custom_snake_tail.html name='freckled' %}
		{% include custom_snake_tail.html name='hook' %}
		{% include custom_snake_tail.html name='pixel' %}
		{% include custom_snake_tail.html name='round-bum' %}
		{% include custom_snake_tail.html name='sharp' %}
		{% include custom_snake_tail.html name='skinny' %}
		{% include custom_snake_tail.html name='small-rattle' %}
	</div>
	<div class="col-sm-1 col-2"></div>
	<div class="col">
		<p><strong>Head Types</strong></p>
		{% include custom_snake_head.html name='regular' %}
		{% include custom_snake_head.html name='beluga' %}
		{% include custom_snake_head.html name='bendr' %}
		{% include custom_snake_head.html name='dead' %}
		{% include custom_snake_head.html name='evil' %}
		{% include custom_snake_head.html name='fang' %}
		{% include custom_snake_head.html name='pixel' %}
		{% include custom_snake_head.html name='safe' %}
		{% include custom_snake_head.html name='sand-worm' %}
		{% include custom_snake_head.html name='shades' %}
		{% include custom_snake_head.html name='silly' %}
		{% include custom_snake_head.html name='smile' %}
		{% include custom_snake_head.html name='tongue' %}
	</div>
</div>

#### Winter Classic 2019 Theme

These customizations were release with the Battlesnake Winter Classic, 2019.

<div class="row">
	<div class="col">
		<p class="text-right"><strong>Tail Types</strong></p>
		{% include custom_snake_tail.html name='bwc-bonhomme' %}
		{% include custom_snake_tail.html name='bwc-flake' %}
		{% include custom_snake_tail.html name='bwc-ice-skate' %}
		{% include custom_snake_tail.html name='bwc-present' %}
	</div>
	<div class="col-sm-1 col-2"></div>
	<div class="col">
		<p><strong>Head Types</strong></p>
		{% include custom_snake_head.html name='bwc-bonhomme' %}
		{% include custom_snake_head.html name='bwc-earmuffs' %}
		{% include custom_snake_head.html name='bwc-rudolph' %}
		{% include custom_snake_head.html name='bwc-scarf' %}
		{% include custom_snake_head.html name='bwc-ski' %}
		{% include custom_snake_head.html name='bwc-snow-worm' %}
		{% include custom_snake_head.html name='bwc-snowman' %}
	</div>
</div>

### Futher Reading

Check out the [Battlesnake API Reference](/snake-api) for more information and examples.
