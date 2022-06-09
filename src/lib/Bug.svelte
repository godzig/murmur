<script>
	import { getContext } from 'svelte';

	const { getCtx } = getContext("context");
	const context = getCtx();

	export let name = 'chirp';
	export let pulse = false;
	export let frequency = 440;
	let type = 'sine';
	let squelch = 2.5;
	let pause = 300;

	function start(){
		if (pulse) {
			beat()
		}
		else {
			note()
		}
	}

	function note(){
		let osc = context.createOscillator();
		let gain = context.createGain();
		osc.connect(gain);
		gain.connect(context.destination);
		osc.frequency.value = frequency;
		osc.type = type;
		osc.start();

		gain.gain.exponentialRampToValueAtTime(
			0.00001, context.currentTime + squelch
		)
	}

	function beat(){
		for (let i=0; i<4; i++){
			note();
			sleep(pause);
		}
	}

	function sleep(milliseconds) {
		const date = Date.now();
		let currentDate = null;
		do {
			currentDate = Date.now()
		} while (currentDate - date < milliseconds)
	}
</script>


<div class="bug">
	<button on:click={start} >{name}</button>
</div>


<style>
	.bug {
		display: inline-block;
		border: 1px solid rgba(0, 0, 0, 0.1);
		margin: 1rem 0;
		margin:  10px;
	}

	.bug button {
		padding: 100px;
		display: inline-block;
		align-items: center;
		justify-content: center;
		border: 0;
		background-color: #333;
		touch-action: manipulation;
		color: var(--text-color);
		font-size: 2rem;
	}
</style>