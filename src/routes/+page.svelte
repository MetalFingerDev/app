<script>
	import Button from '$lib/Button.svelte';
	import Card from '$lib/Card.svelte';
	import Todo from '$lib/Todo.svelte';
	import { Tv } from 'lucide-svelte';
	import Avatar from '$lib/Avatar.svelte';
	import sunnyLeone from '$lib/assets/sideeye.webp';
</script>

<!--html-->

<section>
	<Card
		class="design"
		title="A Sharp heading grabs readers attention"
		subtitle="A muted text color for the subtitle to add more info"
	>
		<footer>
			<div class="button-container">
				<Button variant="pop"><span class="button default">Some action</span></Button>
			</div>
			<div class="button-container">
				<Button href="https://youtu.be/wbTHVS0n-LM?si=HnFv6TTNH8Bq3WCK" variant="ghost"
					><span class="button push"> <Tv /></span></Button
				>
			</div>
		</footer>
	</Card>

	<Card>
		<Todo />
	</Card>

	
	<Avatar src={sunnyLeone} alt="Sunny Leone" fallback="SL" />
</section>

<!--/html-->

<style>
	section {
		margin-top: 4rem;
		display: grid;
		grid-auto-flow:column ;
		place-items: center;
	}

	footer {
		display: grid;
		grid-template-columns: 1fr 1fr;
	}
	.button-container {
		display: grid;
		place-items: center;
	}

	.push {
		padding: 1rem 0;
	}

	.default {
		padding: 1rem;
	}
</style>
