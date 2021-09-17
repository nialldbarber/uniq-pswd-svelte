<script lang="ts">
  import MdVerifiedUser from 'svelte-icons/md/MdVerifiedUser.svelte';
  import MdErrorOutline from 'svelte-icons/md/MdErrorOutline.svelte';
  import MdWarning from 'svelte-icons/md/MdWarning.svelte';
  import MdBatteryChargingFull from 'svelte-icons/md/MdBatteryChargingFull.svelte';

  export let password: string;
  export let background: string;

  const PASSWORD_STRENGTH = {
    mega: 'Mega',
    good: 'Strong',
    medium: 'Fairly strong',
    bad: 'Weak',
  };
</script>

<p>{password}</p>
<div class="icon-container">
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
  <span>{PASSWORD_STRENGTH[background]} password</span>
</div>

<style lang="scss">
  p {
    margin: 0;
    color: var(--white);
    font-size: 3rem;
    font-weight: 500;
    line-height: 1.3;
    margin-bottom: 0.5rem;
    word-break: break-word;
  }

  .icon-container {
    display: flex;
    align-items: center;

    span {
      display: block;
      padding-left: 0.5rem;
      color: var(--white);
      font-size: 1.2rem;
    }
  }

  .icons {
    color: var(--white);
    width: 35px;
    height: 35px;
  }
</style>
