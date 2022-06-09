<script>
	import Bug from '$lib/Bug.svelte';
	import '../app.css';
</script>

<h1>Murmurs</h1>

<Bug frequency={440} />
<Bug frequency={120} name={"boop"}/>
<Bug frequency={200} pulse={true} name={"beat"}/>
<Bug frequency={777} name={"high"}/>

<style>
	h1 {
		font-family: 'Arial';
		font-weight:  200;
	}
</style>