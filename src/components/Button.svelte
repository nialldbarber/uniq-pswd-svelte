<script lang="ts">
  import {copyToClipboard} from '../utils/copyToClipboard';

  export let copyText: string;
</script>

<button on:click={() => copyToClipboard(copyText)}>Copy password</button>

<style lang="scss">
  button {
    filter: drop-shadow(1px 2px 8px hsl(220deg 60% 50% / 0.3))
      drop-shadow(2px 4px 16px hsl(220deg 60% 50% / 0.3))
      drop-shadow(4px 8px 32px hsl(220deg 60% 50% / 0.3));
  }
</style>
