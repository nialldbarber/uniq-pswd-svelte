<script lang="ts">
  import {generatePassword} from './utils/generatePassword';
  import {handleBackgroundChange} from './utils/background';

  import Container from './components/Container.svelte';
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
  <Container>
    <div>
      <Password {password} background={backgroundColor} />
      <Slider {range} {handleChange} />
      <p>Length ({range})</p>
    </div>
    <div class="checkbox-container">
      <Checkbox
        isType={isLetter}
        typeName="letter"
        title="Letters (e.g. Aa)"
        action={() => (isLetter = !isLetter)}
      />
      <Checkbox
        isType={isNumber}
        typeName="number"
        title="Digits (e.g. 345)⁭"
        action={() => (isNumber = !isNumber)}
      />
      <Checkbox
        isType={isSymbol}
        typeName="symbol"
        title="Symbols (@&$!#?)"
        action={() => (isSymbol = !isSymbol)}
      />
    </div>
    <Button copyText={password} />
  </Container>
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

  p {
    margin: 0;
    color: var(--white);
  }

  .checkbox-container {
    display: flex;
    margin-top: 2rem;
  }
</style>
