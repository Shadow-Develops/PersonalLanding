<script>
	let { data } = $props();
</script>

<section id="projects" class="bg-base-200/50 px-4 py-16">
	<div class="mx-auto max-w-4xl">
		<h2 class="mb-12 text-center text-3xl font-bold">{data.title}</h2>
		<div class="grid gap-6 md:grid-cols-2">
			{#each data.items as project}
				<a
					href={project.url}
					target="_blank"
					rel="noopener noreferrer"
					class="card bg-base-100 shadow-lg transition-all hover:-translate-y-1 hover:shadow-xl"
				>
					<div class="card-body">
						<h3 class="card-title text-primary">{project.name}</h3>
						<p class="text-base-content/70">{project.description}</p>
						{#if project.tags && project.tags.length > 0}
							<div class="mt-4 card-actions justify-end">
								{#each project.tags as tag}
									<span class="badge badge-outline badge-sm">{tag}</span>
								{/each}
							</div>
						{/if}
					</div>
				</a>
			{/each}
		</div>
	</div>
</section>
