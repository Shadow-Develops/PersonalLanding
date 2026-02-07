<script>
	import config from '$lib/config';

	// Dynamically import all section components (excluding template)
	const sectionModules = import.meta.glob('$lib/components/sections/*.svelte', { eager: true });
	const sectionComponents = $state({});
	for (const path in sectionModules) {
		const filename = path.split('/').pop().replace('.svelte', '');
		if (!filename.startsWith('_')) {
			const key = filename.charAt(0).toLowerCase() + filename.slice(1);
			sectionComponents[key] = sectionModules[path].default;
		}
	}

	// Import hero variants
	const heroModules = import.meta.glob('$lib/components/sections/hero/*.svelte', { eager: true });
	const heroVariants = $state({});
	for (const path in heroModules) {
		const filename = path.split('/').pop().replace('.svelte', '').replace('Hero', '');
		const key = filename.charAt(0).toLowerCase() + filename.slice(1);
		heroVariants[key] = heroModules[path].default;
	}

	// Import links variants
	const linksModules = import.meta.glob('$lib/components/sections/links/*.svelte', { eager: true });
	const linksVariants = $state({});
	for (const path in linksModules) {
		const filename = path.split('/').pop().replace('.svelte', '').replace('Links', '');
		const key = filename.charAt(0).toLowerCase() + filename.slice(1);
		linksVariants[key] = linksModules[path].default;
	}

	// Import gallery variants
	const galleryModules = import.meta.glob('$lib/components/sections/gallery/*.svelte', {
		eager: true
	});
	const galleryVariants = $state({});
	for (const path in galleryModules) {
		const filename = path.split('/').pop().replace('.svelte', '').replace('Gallery', '');
		const key = filename.charAt(0).toLowerCase() + filename.slice(1);
		galleryVariants[key] = galleryModules[path].default;
	}

	// Import about variants
	const aboutModules = import.meta.glob('$lib/components/sections/about/*.svelte', { eager: true });
	const aboutVariants = $state({});
	for (const path in aboutModules) {
		const filename = path.split('/').pop().replace('.svelte', '').replace('About', '');
		const key = filename.charAt(0).toLowerCase() + filename.slice(1);
		aboutVariants[key] = aboutModules[path].default;
	}

	// Helper function to get the component for a section
	function getComponentForSection(section) {
		const type = section.type;
		const variant = section?.variant;

		switch (type) {
			case 'hero':
				return heroVariants[variant || 'centered'];
			case 'links':
				return linksVariants[variant || 'default'];
			case 'gallery':
				return galleryVariants[variant || 'grid'];
			case 'about':
				return aboutVariants[variant || 'centered'];
			default:
				return sectionComponents[type];
		}
	}

	const enabledSections = $derived(
		config.sections
			.filter((section) => section?.enabled !== false)
			.filter((section) => getComponentForSection(section))
			.map((section, index) => ({
				key: `${section.type}-${index}`,
				component: getComponentForSection(section),
				data: section
			}))
	);

	const footerText = $derived.by(() => {
		const date = new Date().getFullYear();
		let text = config.footerSettings.text
			.replaceAll('{date}', date)
			.replaceAll('{siteName}', config.siteSettings.siteName)
			.replaceAll(/\[([^\]]+)\]\(([^)]+)\)/g, '<a class="link link-hover" href="$2">$1</a>');
		return text;
	});
</script>

<svelte:head>
	<title>{config.siteSettings.siteName}</title>
</svelte:head>

<main class="min-h-screen">
	{#each enabledSections as { component: Component, data, key } (key)}
		<Component {data} />
	{/each}
</main>

{#if config.footerSettings.enabled}
	<footer class="items-center justify-center bg-base-200 p-6 text-center text-base-content">
		<p class="text-sm opacity-70">
			{@html footerText}
		</p>
	</footer>
{/if}
