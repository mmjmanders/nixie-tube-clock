<script lang="ts">
	import '@fontsource-variable/sixtyfour/full.css';
	import './layout.css';
	import favicon from '$lib/assets/favicon.svg';
	import appleTouchIcon from '$lib/assets/apple-touch-icon-180x180.png';
	import { pwaInfo } from 'virtual:pwa-info';

	const { children } = $props();

	const manifest = $derived(pwaInfo?.webManifest.linkTag);
	const registerSW = $derived(pwaInfo?.registerSW?.scriptTag);
</script>

<svelte:head>
	<link rel="icon" href={favicon} sizes="any" type="image/svg+xml" />
	<link rel="apple-touch-icon" href={appleTouchIcon} />
	{#if manifest}
		{@html manifest}
	{/if}
	{#if registerSW}
		{@html registerSW}
	{/if}
</svelte:head>

<main>
	{@render children()}
</main>
