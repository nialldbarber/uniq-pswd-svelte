<script lang="ts">
	import {generatePassword} from './utils/generatePassword';
	import {copyToClipboard} from './utils/copyToClipboard';

	let range: number = 12;
	let pw: string = "";
	let isLetter: boolean = true;
	let isNumber: boolean = true;
	let isSymbol: boolean = false;

	$: pwLength = pw.length;
	$: pwR = generatePassword(range, isLetter, isNumber, isSymbol);
</script>

<main>
	<div>
		<p>{pwR}</p>
		<p>password strength</p>
		<input
			type="range"
			id="range"
			name="password"
			min="0"
			max="40"
			step="1"
			value={range}
			on:change={(e) => (range = e.target.value)}
			style="background: linear-gradient(to right, rgb(255, 255, 255) '{(range) * 2.5}'%, rgba(255, 255, 255, 0.4) 0%)"
		/>
		<p>Length ({pwLength})</p>
		<p>Range is {range}</p>
	</div>

	<div>
		<button on:click={() => (isLetter = !isLetter)}>Letters</button>
		<button on:click={() => (isNumber = !isNumber)}>Numbers</button>
		<button on:click={() => (isSymbol = !isSymbol)}>Symbols</button>
	</div>

	<button on:click={() => copyToClipboard(pwR)}>Copy password</button>
</main>

<style>
	p {
		margin: 0;
		color: purple;
	}
</style>
