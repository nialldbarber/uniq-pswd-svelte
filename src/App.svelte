<script lang="ts">
  import {generatePassword} from './utils/generatePassword';
  import {handleBackgroundChange} from './utils/background';

  import Checkbox from './components/Checkboxes.svelte';
  import Button from './components/Button.svelte';
  import Slider from './components/Slider.svelte';

  let range: number = 12;
  let isLetter: boolean = true;
  let isNumber: boolean = true;
  let isSymbol: boolean = false;

  function handleChange(e: Event) {
    const value = (<HTMLInputElement>e.target).value;
    range = parseInt(value);
  }

  $: backgroundColor = handleBackgroundChange(range);
  $: password = generatePassword(range, isLetter, isNumber, isSymbol);
</script>

<main class={backgroundColor}>
  <div>
    <p>{password}</p>
    <p>password strength</p>
    <Slider {range} {handleChange} />
    <p>Length ({range})</p>
    <p>{backgroundColor}</p>
  </div>

  <div>
    <Checkbox
      isType={isLetter}
      typeName="letter"
      action={() => (isLetter = !isLetter)}
    />
    <Checkbox
      isType={isNumber}
      typeName="number"
      action={() => (isNumber = !isNumber)}
    />
    <Checkbox
      isType={isSymbol}
      typeName="symbol"
      action={() => (isSymbol = !isSymbol)}
    />
  </div>
  <Button copyText={password} />
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
</style>
