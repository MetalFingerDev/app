<script lang="ts">
	import { onMount } from 'svelte';
	import { Sun, Moon } from 'lucide-svelte';
	import Button from './Button.svelte';

	let mode = $state<'light' | 'dark'>('dark');

	onMount(() => {
		const localMode = document.documentElement.getAttribute('data-theme') as 'light' | 'dark';
		if (localMode) {
			mode = localMode;
		}
	});

	$effect(() => {
		const root = document.documentElement;
		root.setAttribute('data-theme', mode);
		root.classList.toggle('dark', mode === 'dark');
		root.style.colorScheme = mode;

		localStorage.setItem('theme', mode);
	});

	function toggle() {
		mode = mode === 'light' ? 'dark' : 'light';
	}
</script>

<Button
	onclick={toggle}
	variant="outline"
	aria-label="Toggle {mode === 'light' ? 'Dark' : 'Light'} Mode"
	class="mode-toggle"
	style="
			display: inline-block
			place-items: center;
			padding: 0.5rem;"
>
	{#if mode === 'light'}
		<Sun id="theme-toggle-icon" />
	{:else}
		<Moon id="theme-toggle-icon" />
	{/if}
</Button>

<style>
	:global(#theme-toggle-icon) {
		animation: fade-in var(--time) ease-out;
	}

	@keyframes fade-in {
		from {
			opacity: 0;
			transform: scale(0.8);
		}
		to {
			opacity: 1;
			transform: scale(1);
		}
	}
</style>
