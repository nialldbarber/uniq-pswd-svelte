<script lang="ts">
  export let range: number;
  export let handleChange: (e: Event) => void;
</script>

<input
  type="range"
  id="range"
  name="password"
  class="slider"
  min="0"
  max="40"
  step="1"
  value={range}
  on:input={handleChange}
  style="background: linear-gradient(to right, rgb(255, 255, 255) {range *
    2.5}%, rgba(255, 255, 255, 0.4) 0%)"
/>

<style lang="scss">
  .slider {
    align-self: center;
    appearance: none;
    width: 100%;
    border-radius: 8px;
    border: none;
    height: 8px;
    cursor: pointer;

    &[type='range'] {
      &::-webkit-slider-thumb {
        appearance: none;
        height: 35px;
        width: 35px;
        border-radius: 50%;
        background: var(--white);
        border: none;
        cursor: pointer;
      }
    }

    &[type='range' i] {
      color: var(--white);
    }
  }
</style>
