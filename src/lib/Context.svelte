<script>
  
	import { onMount, setContext } from 'svelte';
	import { AudioContext } from "standardized-audio-context"

  let context;

  setContext("context", {
    getCtx: () => context,
  });

  onMount(() => {
    context = new AudioContext();
  });

</script> 

<div>
  {#if context}
    <slot />
  {/if}
</div>