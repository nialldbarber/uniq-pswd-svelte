<script lang="ts">
  import {generatePassword} from './utils/generatePassword';
  import {handleBackgroundChange} from './utils/background';

  import Checkbox from './components/Checkboxes.svelte';
  import Button from './components/Button.svelte';
  import Slider from './components/Slider.svelte';
  import Password from './components/Password.svelte';

  let range: number = 12;
  let isLetter: boolean = true;
  let isNumber: boolean = true;
  let isSymbol: boolean = false;

  function handleChange(e: Event): void {
    const value = (<HTMLInputElement>e.target).value;
    range = parseInt(value);
  }

  $: backgroundColor = handleBackgroundChange(range);
  $: password = generatePassword(range, isLetter, isNumber, isSymbol);
</script>

<main class={backgroundColor}>
  <div class="container">
    <div>
      <Password {password} background={backgroundColor} />
      <Slider {range} {handleChange} />
      <p>Length ({range})</p>
    </div>

    <div class="checkbox-container">
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
  </div>
</main>

<style lang="scss">
  main {
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;

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

  .container {
    position: relative;
    display: flex;
    align-self: center;
    flex-direction: column;
    justify-content: center;
    width: 100%;
    height: 300px;
    padding: 2.5rem 5rem;
  }

  p {
    margin: 0;
    color: var(--white);
  }

  .checkbox-container {
    display: flex;
    margin-top: 2rem;
  }
</style>
