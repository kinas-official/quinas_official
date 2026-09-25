<script lang="ts">
	import './layout.css';
	import './main.css';
	import favicon from '$lib/assets/favicon.svg';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href="/favicon.ico" sizes="32x32" />
	<link rel="icon" href={favicon} type="image/svg+xml" />
	<link rel="apple-touch-icon" href="/apple-touch-icon.png" />
	<link rel="manifest" href="/site.webmanifest" />
	<meta name="theme-color" content="#000000" />
</svelte:head>
{@render children()}
