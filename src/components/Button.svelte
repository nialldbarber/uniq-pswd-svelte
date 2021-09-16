<script lang="ts">
  import {copyToClipboard} from '../utils/copyToClipboard';

  export let copyText: string;
</script>

<button on:click={() => copyToClipboard(copyText)}>Copy password</button>

<style lang="scss">
  button {
    position: absolute;
    top: 2.5rem;
    right: 5rem;
    width: 180px;
    background: var(--green);
    color: var(--white);
    border: 2px solid var(--white);
    padding: 1.125rem 1rem;
    font-size: 1.125rem;
    border-radius: 5px;
    transition: background 0.125s ease 0s, color 0.125s ease 0s,
      box-shadow 0.2s cubic-bezier(0, 0, 0.38, 0.9);
    user-select: none;
    cursor: pointer;

    filter: drop-shadow(1px 2px 8px hsl(220deg 60% 50% / 0.3))
      drop-shadow(2px 4px 16px hsl(220deg 60% 50% / 0.3))
      drop-shadow(4px 8px 32px hsl(220deg 60% 50% / 0.3));

    &:hover {
      background: var(--white);
      color: var(--green);
    }

    &:focus {
      box-shadow: rgba(66, 153, 225, 0.6) 0px 0px 0px 3px;
    }
  }
</style>
