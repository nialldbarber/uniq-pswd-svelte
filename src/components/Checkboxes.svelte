<script lang="ts">
  export let isType: boolean;
  export let typeName: string;
  export let action: () => void;
</script>

<input
  type="checkbox"
  class="{isType && typeName}"
  id={typeName}
  checked={isType}
  on:click={action}
/>
<label for={typeName}>{typeName}</label>
