<script>
	import './layout.css';
	import { onMount } from 'svelte';
	import { page } from '$app/stores';
	import { fade } from 'svelte/transition';
	import config from '$lib/config';
	import Loader from '$lib/components/Loader.svelte';
	let { children } = $props();

	let activeUrl = $derived($page.url.pathname);

	let isLoading = $state(true);
	onMount(() => {
		const minLoadTime = 500;
		const startTime = Date.now();
		const checkReady = () => {
			const elapsedTime = Date.now() - startTime;
			const remainingTime = Math.max(0, minLoadTime - elapsedTime);

			setTimeout(() => {
				isLoading = false;
			}, remainingTime);
		};
		if (document.readyState === 'complete') {
			checkReady();
		} else {
			window.addEventListener('load', checkReady);
			return () => window.removeEventListener('load', checkReady);
		}

		//? Console Alert Messages
		console.log(
			"%cPersonal Landing Page %cis designed by %cShadow Development%c.\nGet Free: %chttps://shadowdevs.com/store/personallanding\n\n%c⚠️ WARNING: Do not paste any code here unless you know what you're doing!\n%cIf you encounter any errors, please contact support (https://shadowdevs.com/contactus).",
			'font-size: 18px; color: #3b82f6; font-weight: bold;',
			'font-size: 18px; color: #fff; font-weight: bold;',
			'font-size: 18px; color: #3b82f6; font-weight: bold;',
			'font-size: 13px; color: #fff;',
			'font-size: 13px; color: #60a5fa;',
			'color: #fbbf24; font-weight: bold;',
			'color: #9ca3af;'
		);
	});

	function getPageTitle(str) {
		return str
			.replace('/', '')
			.replace(/\//g, ' - ')
			.split(' ')
			.map((word) => word.charAt(0).toUpperCase() + word.slice(1))
			.join(' ');
	}
</script>

<svelte:head>
	{#if activeUrl === '/'}
		<meta property="og:title" content={config.siteSettings.siteName} />
		<meta name="description" content={config.siteSettings.siteDescription} />
		<meta property="og:description" content={config.siteSettings.siteDescription} />
		<meta name="twitter:description" content={config.siteSettings.siteDescription} />
	{:else}
		<meta property="og:title" content={getPageTitle(activeUrl)} />
		<meta name="description" content={config.siteSettings.siteDescription} />
		<meta property="og:description" content={config.siteSettings.siteDescription} />
		<meta name="twitter:description" content={config.siteSettings.siteDescription} />
		<meta property="og:site_name" content={config.siteSettings.siteName} />
	{/if}
	<meta name="theme-color" content={config.siteSettings.metaColor} />
	<meta property="og:url" content={config.domain} />
	<meta property="og:type" content="website" />
	<meta name="twitter:card" content="summary_large_image" />
	<meta property="twitter:domain" content={config.domain} />
	<meta name="language" content="English" />
	<meta name="revisit-after" content="10 days" />
	<meta name="robots" content="index, follow" />

	{#if isLoading}
		<title>Loading...</title>
	{/if}
</svelte:head>

{#if isLoading}
	<Loader />
{:else}
	{#key activeUrl}
		<main in:fade|global={{ duration: 300 }}>
			{@render children()}
		</main>
	{/key}
{/if}
