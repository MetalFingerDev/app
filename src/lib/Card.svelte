<script lang="ts">
	let {
		children,
		title = '',
		subtitle = '',
		titleRef = $bindable(),
		subtitleRef = $bindable(),
		class: className = ''
	} = $props();
</script>

<article class={className}>
	{#if title}
		<header>
			<h2 bind:this={titleRef}>{title}</h2>
			<p bind:this={subtitleRef}>{subtitle}</p>
		</header>
	{/if}
	{@render children?.()}
</article>

<style>
	article {
		display: flex;
		flex-direction: column;
		padding: 2rem;
		gap: 2rem;
		margin: 1rem;

		background: var(--gradient-embose);
		border: 2px solid var(--border);
		border-radius: var(--radius);
		box-shadow: var(--shadow);
	}

	article:hover {
		background: var(--gradient-pull);
		border-top-color: var(--glint);
	}

	p {
		color: var(--muted);
	}
</style>
