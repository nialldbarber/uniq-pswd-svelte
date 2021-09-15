<script lang="ts">
  import MdVerifiedUser from 'svelte-icons/md/MdVerifiedUser.svelte';
  import MdErrorOutline from 'svelte-icons/md/MdErrorOutline.svelte';
  import MdWarning from 'svelte-icons/md/MdWarning.svelte';
  import MdBatteryChargingFull from 'svelte-icons/md/MdBatteryChargingFull.svelte';

  export let password: string;
  export let background: string;
</script>

<p class="password">{password}</p>
<div class="icons">
  {#if background === 'bad'}
    <MdWarning />
  {:else if background === 'medium'}
    <MdErrorOutline />
  {:else if background === 'good'}
    <MdVerifiedUser />
  {:else if background === 'mega'}
    <MdBatteryChargingFull />
  {/if}
</div>

<style>
  .password {
    margin: 0;
    color: var(--white);
    font-size: 3rem;
    font-weight: 500;
    line-height: 1.3;
    margin-bottom: 0.5rem;
    word-break: break-word;
  }

  .icons {
    color: var(--white);
    width: 35px;
    height: 35px;
  }
</style>
