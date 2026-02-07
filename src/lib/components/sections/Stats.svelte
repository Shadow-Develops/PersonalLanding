<script>
	let { data } = $props();
</script>

<section id="stats" class="px-4 py-16">
	<div class="mx-auto max-w-4xl">
		{#if data.title}
			<h2 class="mb-12 text-center text-3xl font-bold">{data.title}</h2>
		{/if}
		<div class="stats w-full stats-vertical bg-base-100 shadow lg:stats-horizontal">
			{#each data.items as stat}
				<div class="stat place-items-center">
					<div class="stat-title">{stat.label}</div>
					<div class="stat-value text-primary">{stat.value}</div>
					{#if stat.description}
						<div class="stat-desc">{stat.description}</div>
					{/if}
				</div>
			{/each}
		</div>
	</div>
</section>
