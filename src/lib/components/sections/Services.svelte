<script>
	let { data } = $props();

	const defaultIcons = {
		code: `<svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="16 18 22 12 16 6"/><polyline points="8 6 2 12 8 18"/></svg>`,
		design: `<svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 19l7-7 3 3-7 7-3-3z"/><path d="M18 13l-1.5-7.5L2 2l3.5 14.5L13 18l5-5z"/><path d="M2 2l7.586 7.586"/><circle cx="11" cy="11" r="2"/></svg>`,
		consulting: `<svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"/></svg>`,
		default: `<svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polygon points="12 2 2 7 12 12 22 7 12 2"/><polyline points="2 17 12 22 22 17"/><polyline points="2 12 12 17 22 12"/></svg>`
	};

	function getIcon(iconName) {
		return defaultIcons[iconName] || defaultIcons.default;
	}
</script>

<section id="services" class="bg-base-200/50 px-4 py-16">
	<div class="mx-auto max-w-5xl">
		<h2 class="mb-12 text-center text-3xl font-bold">{data.title}</h2>
		<div class="grid gap-6 md:grid-cols-2 lg:grid-cols-3">
			{#each data.items as service}
				<div class="card bg-base-100 shadow-lg transition-shadow hover:shadow-xl">
					<div class="card-body items-center text-center">
						<div class="mb-4 text-primary">
							{@html getIcon(service.icon)}
						</div>
						<h3 class="card-title">{service.name}</h3>
						<p class="text-base-content/70">{service.description}</p>
					</div>
				</div>
			{/each}
		</div>
	</div>
</section>
