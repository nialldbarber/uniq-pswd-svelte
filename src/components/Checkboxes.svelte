<script lang="ts">
  export let isType: boolean;
  export let typeName: string;
  export let action: () => void;
</script>

<div>
  <input
    type="checkbox"
    class={isType && typeName}
    id={typeName}
    checked={isType}
    on:click={action}
  />
  <label for={typeName}>{typeName}</label>
</div>

<style lang="scss">
  div {
    margin: 0;
    color: var(--white);
    font-size: 1.2rem;
    margin-right: 0.7rem;
    cursor: pointer;
  }

  label {
    display: inline-block;
    margin-left: 0.5rem;
    color: var(--white);
    font-size: 1.2rem;
    user-select: none;
  }
</style>
