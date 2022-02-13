<script lang="ts">
	import Header from '$lib/header/Header.svelte';
	import '../app.css';
</script>

<svelte:head>
	<title>Delphi Project</title>
	<link rel="stylesheet" href="node_modules/svelte-material-ui/bare.css" />
</svelte:head>

<Header />

<main>
	<slot />
</main>

<footer>
	<a href="https://github.com/thedelphiproject">Github</a>
</footer>

<style>
	main {
		flex: 1;
		display: flex;
		flex-direction: column;
		padding: 1rem;
		width: 100%;
		max-width: 1024px;
		margin: 0 auto;
		box-sizing: border-box;
	}

	footer {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		padding: 40px;
	}

	footer a {
		font-weight: bold;
	}

	@media (min-width: 480px) {
		footer {
			padding: 40px 0;
		}
	}
</style>
