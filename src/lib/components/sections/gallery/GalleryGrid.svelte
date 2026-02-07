<script>
	let { data } = $props();
</script>

<section id="gallery" class="bg-base-200/50 px-4 py-16">
	<div class="mx-auto max-w-5xl">
		<h2 class="mb-12 text-center text-3xl font-bold">{data.title}</h2>
		<div class="grid grid-cols-2 gap-4 md:grid-cols-3 lg:grid-cols-4">
			{#each data.items as item}
				{#if item.url}
					<a href={item.url} target="_blank" rel="noopener noreferrer" class="group">
						<figure class="relative aspect-square overflow-hidden rounded-lg">
							<img
								src={item.image}
								alt={item.caption || ''}
								class="h-full w-full object-cover transition-transform group-hover:scale-110"
							/>
							{#if item.caption}
								<figcaption
									class="absolute inset-0 flex items-center justify-center bg-black/60 p-4 opacity-0 transition-opacity group-hover:opacity-100"
								>
									<span class="text-center text-sm text-white">{item.caption}</span>
								</figcaption>
							{/if}
						</figure>
					</a>
				{:else}
					<figure class="group relative aspect-square overflow-hidden rounded-lg">
						<img
							src={item.image}
							alt={item.caption || ''}
							class="h-full w-full object-cover transition-transform group-hover:scale-105"
						/>
						{#if item.caption}
							<figcaption
								class="absolute inset-0 flex items-center justify-center bg-black/60 p-4 opacity-0 transition-opacity group-hover:opacity-100"
							>
								<span class="text-center text-sm text-white">{item.caption}</span>
							</figcaption>
						{/if}
					</figure>
				{/if}
			{/each}
		</div>
	</div>
</section>
