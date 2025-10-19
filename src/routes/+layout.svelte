<script lang="ts">
	import '../app.css';

	let { children } = $props();
</script>

<svelte:head>
	<title>Thinh Nguyen</title>
</svelte:head>

{@render children?.()}
