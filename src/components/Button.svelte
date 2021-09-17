<script lang="ts">
  import {copyToClipboard} from '../utils/copyToClipboard';

  export let copyText: string;
</script>

<div>
  <span>Copied</span>
  <button on:click={() => copyToClipboard(copyText)}>Copy password</button>
</div>

<style lang="scss">
  div {
    position: absolute;
    top: 2.5rem;
    right: 5rem;
  }

  span {
    position: absolute;
    top: -2.5rem;
    left: 50%;
    transform: translateX(-50%);
    background: var(--black);
    color: var(--white);
    padding: 0.5rem;
    border-radius: 5px;
    font-size: 0.8rem;

    &:after {
      content: '';
      position: 'absolute';
      display: block;
      left: 50%;
      top: 30px;
      border-left: 5px solid transparent;
      border-right: 5px solid transparent;
      border-top: 5px solid var(--white);
      transform: translateX(-50%);
    }
  }

  button {
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
