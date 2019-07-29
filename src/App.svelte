<script>
	import Display from './Display.svelte';
	import Hangman from './Hangman.svelte';
	import words from './words';

	const GAME_STATES = {
		PLAYING: 'PLAYING',
		WON: 'WON',
		LOST: 'LOST'
	}

	let word = '';
	let revealed = [];
	let lifes = 6;
	let gameState = '';

	function start() {
		word = words[Math.floor(Math.random() * words.length)].toUpperCase();
		gameState = GAME_STATES.PLAYING
		lifes = 6;
		revealed = Array.from({length: word.length });
	}

	function decrementLifes() {
		lifes -= 1
		if (!lifes) {
			gameState = GAME_STATES.LOST;
		}
	}

	window.addEventListener('keydown', ({ key }) => {
		if (key.match(/^[a-z]$/i)) {
			let wrongLetter = true;
			for (const i in word) {
				if (word[i] == key.toUpperCase()) {
					revealed[i] = true;
					wrongLetter = false
				}
			}
			if (wrongLetter) decrementLifes();
			else if (revealed.every(i=>i)) {
				gameState = GAME_STATES.WON
			}
		}
	})

</script>

<style>
	main {
		position: relative;
		top: 50%;
		left: 50%;
		transform: translate(-50%,-50%);
		/* padding: 50px; */
		width: fit-content;
		border-width: 4px;
		border-color:black;
		border-style: dashed solid;
		text-align: center;
	}

	button {
		background-color: #0000;
		border: 3px solid black;
		color: #000;
		font-size: 1.4em;
	}


	h2 {
		font-size: 1.7em;
	}

	p {
		font-size: 1.5em;
	}
</style>

<main>
<h2>Hangman game</h2>
<Hangman {lifes} />
{#if gameState === GAME_STATES.PLAYING}
	<p>Lifes: {lifes}</p>
	<Display {word} {revealed} />
{:else}	
	{#if gameState === GAME_STATES.WON}
	<p>You won!</p>
	{:else if gameState === GAME_STATES.LOST}
	<p>You lost!</p>
	{/if}
	<button on:click={start}>Start Game</button>
{/if}
</main>