<script lang="ts">
  export let isType: boolean;
  export let typeName: string;
  export let title: string;
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
  <label for={typeName}>{title}</label>
</div>

<style lang="scss">
  div {
    margin: 0 0.7rem 0 0;
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
