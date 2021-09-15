<script lang="ts">
  import {copyToClipboard} from '../utils/copyToClipboard';

  export let copyText: string;
</script>

<button on:click={() => copyToClipboard(copyText)}>Copy password</button>
