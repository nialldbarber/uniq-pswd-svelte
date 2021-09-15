<script lang="ts">
	import {generatePassword} from './utils/generatePassword';
	import {copyToClipboard} from './utils/copyToClipboard';
	import {handleBackgroundChange} from './utils/background';

	let range: number = 12;
	let isLetter: boolean = true;
	let isNumber: boolean = true;
	let isSymbol: boolean = false;

	function handleChange(e: Event) {
		const value = (<HTMLInputElement>e.target).value
		range = parseInt(value);
	}

	$: backgroundColor = handleBackgroundChange(range);
	$: pwR = generatePassword(range, isLetter, isNumber, isSymbol);
</script>

<main class="{backgroundColor}">
	<div>
		<p>{pwR}</p>
		<p>password strength</p>
		<input
			type="range"
			id="range"
			name="password"
			class="slider"
			min="0"
			max="40"
			step="1"
			value={range}
			on:change={handleChange}
			style="background: linear-gradient(to right, rgb(255, 255, 255) {range * 2.5}%, rgba(255, 255, 255, 0.4) 0%)"
		/>
		<p>Length ({range})</p>
		<p>{backgroundColor}</p>
	</div>

	<div>
		<input
			type="checkbox"
			class="{isLetter && 'letter'}"
			id="letters"
			on:click={() => (isLetter = !isLetter)}
		/>
		<label for="letters">Letters</label>
		<button
			class="{isNumber && 'number'}"
			on:click={() => (isNumber = !isNumber)}
		>
			Numbers
		</button>
		<button
			class="{isSymbol && 'symbol'}"
			on:click={() => (isSymbol = !isSymbol)}
		>
			Symbols
		</button>
	</div>

	<button on:click={() => copyToClipboard(pwR)}>Copy password</button>
</main>

<style lang="scss">
	main {
		background: var(--black);

		&.mega {
			background: var(--mega);
		}
		&.good {
			background: var(--good);
		}
		&.medium {
			background: var(--medium);
		}
		&.bad {
			background: var(--bad);
		}
	}

	p {
		margin: 0;
		color: var(--white);
	}

	button {
		color: var(--white);

		&.letter {
			background: red;
		}
		&.number {
			background: blue;
		}
		&.symbol {
			background: green;
		}
	}

	.slider {
		align-self: center;
    appearance: none;
    width: 100%;
    border-radius: 8px;
    height: 8px;
    cursor: pointer;
	}
</style>
