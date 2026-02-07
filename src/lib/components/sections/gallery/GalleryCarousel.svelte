<script>
	let { data } = $props();

	let currentIndex = $state(0);

	function next() {
		currentIndex = (currentIndex + 1) % data.items.length;
	}

	function prev() {
		currentIndex = (currentIndex - 1 + data.items.length) % data.items.length;
	}

	function goTo(index) {
		currentIndex = index;
	}
</script>

<section id="gallery" class="bg-base-200/50 px-4 py-16">
	<div class="mx-auto max-w-4xl">
		<h2 class="mb-12 text-center text-3xl font-bold">{data.title}</h2>

		<div class="relative">
			<div class="carousel w-full">
				{#each data.items as item, index}
					<div class="relative carousel-item w-full" class:hidden={currentIndex !== index}>
						<figure class="relative w-full">
							{#if item.url}
								<a href={item.url} target="_blank" rel="noopener noreferrer">
									<img
										src={item.image}
										alt={item.caption || ''}
										class="w-full rounded-lg object-cover"
										style="max-height: 600px;"
									/>
								</a>
							{:else}
								<img
									src={item.image}
									alt={item.caption || ''}
									class="w-full rounded-lg object-cover"
									style="max-height: 600px;"
								/>
							{/if}
							{#if item.caption}
								<figcaption class="mt-4 text-center text-base-content/70">
									{item.caption}
								</figcaption>
							{/if}
						</figure>
					</div>
				{/each}
			</div>

			<div class="absolute top-1/2 right-5 left-5 flex -translate-y-1/2 transform justify-between">
				<button onclick={prev} class="btn btn-circle btn-sm">❮</button>
				<button onclick={next} class="btn btn-circle btn-sm">❯</button>
			</div>
		</div>

		<div class="mt-6 flex justify-center gap-2">
			{#each data.items as _, index}
				<button
					onclick={() => goTo(index)}
					class="h-2 w-2 rounded-full transition-all {currentIndex === index
						? 'w-8 bg-primary'
						: 'bg-base-content/30'}"
					aria-label="Go to image {index + 1}"
				></button>
			{/each}
		</div>
	</div>
</section>
