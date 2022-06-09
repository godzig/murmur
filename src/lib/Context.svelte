<script>
  // from https://svelte.dev/tutorial/context-api
  
	import { setContext } from 'svelte';
	import { AudioContext } from "standardized-audio-context"

  setContext("context", {
    getCtx: () => context,
  });

  let context;

  function load() {
    context = new AudioContext();
  }

</script> 