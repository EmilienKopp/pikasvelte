<script>
	import { Pikaday } from '$lib';
	import '$lib/pikaday.css';
	import { onMount } from 'svelte';

	let picker;
	let inputElement;

	onMount(() => {
		if (inputElement) {
			picker = new Pikaday({ field: inputElement });
		}

		return () => {
			if (picker) {
				picker.destroy();
			}
		};
	});
</script>

<svelte:head>
	<title>Pikasvelte - Svelte 5 Datepicker</title>
</svelte:head>

<main>
	<h1>Pikasvelte</h1>
	<p>A refreshing Svelte 5 Datepicker — lightweight, no dependencies, modular CSS</p>
	
	<section>
		<h2>Basic Example</h2>
		<label for="datepicker">Select a date:</label>
		<input type="text" id="datepicker" bind:this={inputElement} placeholder="Click to select a date" />
	</section>
</main>

<style>
	main {
		max-width: 800px;
		margin: 0 auto;
		padding: 2rem;
		font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
	}

	h1 {
		color: #333;
	}

	section {
		margin-top: 2rem;
		padding: 1rem;
		border: 1px solid #eee;
		border-radius: 8px;
	}

	label {
		display: block;
		margin-bottom: 0.5rem;
		font-weight: 500;
	}

	input {
		padding: 0.5rem;
		font-size: 1rem;
		border: 1px solid #ccc;
		border-radius: 4px;
		width: 200px;
	}
</style>
