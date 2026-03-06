<script lang="ts">
	import favicon from '$lib/assets/favicon.svg';
	import '../app.css';

	import { PUBLIC_CONVEX_URL } from '$env/static/public';
	import { setupConvex } from 'convex-svelte';
	setupConvex(PUBLIC_CONVEX_URL);

	import ModeToggle from '$lib/ModeToggle.svelte';

	let { children } = $props();
</script>

<!--html-->

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<header>
	<ModeToggle />

</header>

{@render children()}

<!--/html-->

<style>
	header {
		display: flex;
		align-items: center;
		justify-content: center;
		gap: 2rem;
		padding: 1rem;
	}
</style>
