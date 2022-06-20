<script>
	import Layout from './../../.svelte-kit/runtime/components/layout.svelte';
	import '../app.css';
	let checked = true;
	//handels route
</script>

<header>Layout</header>
<input type="checkbox" bind:checked />

<slot />

<footer>footer</footer>
