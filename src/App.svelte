<script lang="ts">
	import { invoke } from "@tauri-apps/api";

	export let name: string;
	let messagePromise = invoke("hello_command", { name });
</script>

<main>
	{#await messagePromise}
		<h1>Loading.invoke.</h1>
	{:then message}
		<h1>{message}</h1>
	{:catch err}
		<h1>{err}</h1>
	{/await}
	<p>
		Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn
		how to build Svelte apps.
	</p>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
