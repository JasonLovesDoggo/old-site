<script lang="ts">
	import { COLS, ROWS } from "../../utils";

	import { Tile } from "../board";
	import {createEventDispatcher} from "svelte";
	const dispatch = createEventDispatcher();
	export let visible: boolean;
</script>

<h1>how to play</h1>
<div>Guess the <strong>FOODLE</strong> in {ROWS} tries.</div>
<div>Each guess must be a valid {COLS} letter word. Hit the enter button to submit.</div>
<div>
	After each guess, the color of the tiles will change to show how close your guess was to the
	word.
</div>
<div class:complete={visible} class="examples">
	<div><strong>Examples</strong></div>
	<div class="row">
		<Tile value="T" state="🟩" />
		<Tile value="a" state="🔳" />
		<Tile value="c" state="🔳" />
		<Tile value="o" state="🔳" />
		<Tile value="s" state="🔳" />
	</div>
	<div>The letter <strong>T</strong> is in the word and in the correct spot.</div>
	<div class="row">
		<Tile value="p" state="🔳" />
		<Tile value="i" state="🟨" />
		<Tile value="z" state="🔳" />
		<Tile value="z" state="🔳" />
		<Tile value="a" state="🔳" />
	</div>
	<div>The letter <strong>I</strong> is in the word but in the wrong spot.</div>
	<div class="row">
		<Tile value="b" state="🔳"/>
		<Tile value="r" state="🔳"/>
		<Tile value="e" state="🔳"/>
		<Tile value="a" state="🔳"/>
		<Tile value="d" state="⬛"/>
	</div>
	<div>The letter <strong>D</strong> is not in the word in any spot.</div>
</div>
<div>
	This is a recreation of the original <a
		href="https://www.nytimes.com/games/wordle/"
		target="_blank">Wordle</a
>


	by Josh Wardle with a different theme and additional modes and features.
	<br/>
	Please <span on:click={() => dispatch("contact")} style="text-decoration: underline;">contact</span> the developer
	<a href="https://github.com/JasonLovesDoggo" target="_blank">Jason</a>.
	if you have any problems. Or find us on <a class="social_link twitter" href="https://twitter.com/FoodleTheGame">Twitter</a>
	<br/>
	Open the settings menu to see some of the additional features.
	Or click
	<a href="https://jasoncodes.ca/" target="_blank">Here to go home.</a>
	Or view the <span on:click={() => dispatch("changelog")} style="text-decoration: underline;">ChangeLog.</span>
</div>

<style lang="scss">
	* {
		align-content: center;
	}

	div {
		margin: 14px 0;
	}

	.examples {
		border-top: 1px solid var(--border-primary);
		border-bottom: 1px solid var(--border-primary);

		:global(.row > *) {
			height: 100%;
			aspect-ratio: 1;
		}

		&:not(.complete) :global(.row .back) {
			transition-delay: 0.3s;
		}
	}

	.row {
		height: 40px;
		display: flex;
		gap: 4px;
	}


	.twitter:hover {
		color: #00acee
	}

	.social_link {
		-webkit-transition: color 0.4s ease-out;
		-moz-transition: color 0.4s ease-out;
		-o-transition: color 0.4s ease-out;
		-ms-transition: color 0.4s ease-out;
		transition: color 0.4s ease-out;
	}

	.social_link:hover {
		font-size: 15px;
	}

</style>

