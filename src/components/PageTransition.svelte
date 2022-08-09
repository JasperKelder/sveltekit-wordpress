<script>
  import { fade } from 'svelte/transition';
  export let pathname = '';
</script>

{#key pathname}
  <div transition:fade>
    <slot />
  </div>
{/key}
