<script>
	let { data } = $props();

	let lightboxOpen = $state(false);
	let currentImageIndex = $state(0);

	function openLightbox(index) {
		currentImageIndex = index;
		lightboxOpen = true;
		document.body.style.overflow = 'hidden';
	}

	function closeLightbox() {
		lightboxOpen = false;
		document.body.style.overflow = '';
	}

	function nextImage() {
		currentImageIndex = (currentImageIndex + 1) % data.items.length;
	}

	function prevImage() {
		currentImageIndex = (currentImageIndex - 1 + data.items.length) % data.items.length;
	}

	function handleKeydown(event) {
		if (!lightboxOpen) return;
		if (event.key === 'Escape') closeLightbox();
		if (event.key === 'ArrowRight') nextImage();
		if (event.key === 'ArrowLeft') prevImage();
	}
</script>

<svelte:window onkeydown={handleKeydown} />

<section id="gallery" class="bg-base-200/50 px-4 py-16">
	<div class="mx-auto max-w-5xl">
		<h2 class="mb-12 text-center text-3xl font-bold">{data.title}</h2>
		<div class="grid grid-cols-2 gap-4 md:grid-cols-3 lg:grid-cols-4">
			{#each data.items as item, index}
				<button
					onclick={() => openLightbox(index)}
					class="group cursor-pointer border-0 bg-transparent p-0"
				>
					<figure class="relative aspect-square overflow-hidden rounded-lg">
						<img
							src={item.image}
							alt={item.caption || ''}
							class="h-full w-full object-cover transition-transform group-hover:scale-110"
						/>
						<div
							class="absolute inset-0 flex items-center justify-center bg-black/40 opacity-0 transition-opacity group-hover:opacity-100"
						>
							<svg
								xmlns="http://www.w3.org/2000/svg"
								class="h-8 w-8 text-white"
								fill="none"
								viewBox="0 0 24 24"
								stroke="currentColor"
							>
								<path
									stroke-linecap="round"
									stroke-linejoin="round"
									stroke-width="2"
									d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0zM10 7v3m0 0v3m0-3h3m-3 0H7"
								/>
							</svg>
						</div>
					</figure>
				</button>
			{/each}
		</div>
	</div>
</section>

{#if lightboxOpen}
	<div
		class="fixed inset-0 z-50 flex items-center justify-center bg-black/95"
		onclick={closeLightbox}
		onkeydown={(e) => e.key === 'Enter' && closeLightbox()}
		role="dialog"
		aria-modal="true"
		tabindex="-1"
	>
		<button
			onclick={closeLightbox}
			class="btn absolute top-4 right-4 btn-circle text-white btn-ghost"
			aria-label="Close lightbox"
		>
			<svg
				xmlns="http://www.w3.org/2000/svg"
				class="h-6 w-6"
				fill="none"
				viewBox="0 0 24 24"
				stroke="currentColor"
			>
				<path
					stroke-linecap="round"
					stroke-linejoin="round"
					stroke-width="2"
					d="M6 18L18 6M6 6l12 12"
				/>
			</svg>
		</button>

		<button
			onclick={(e) => {
				e.stopPropagation();
				prevImage();
			}}
			class="btn absolute left-4 btn-circle text-white btn-ghost"
			aria-label="Previous image"
		>
			<svg
				xmlns="http://www.w3.org/2000/svg"
				class="h-8 w-8"
				fill="none"
				viewBox="0 0 24 24"
				stroke="currentColor"
			>
				<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
			</svg>
		</button>

		<div
			class="mx-auto max-h-[90vh] max-w-[90vw]"
			onclick={(e) => e.stopPropagation()}
			onkeydown={(e) => e.stopPropagation()}
			role="presentation"
		>
			<img
				src={data.items[currentImageIndex].image}
				alt={data.items[currentImageIndex].caption || ''}
				class="max-h-[90vh] w-auto object-contain"
			/>
			{#if data.items[currentImageIndex].caption}
				<p class="mt-4 text-center text-white">{data.items[currentImageIndex].caption}</p>
			{/if}
		</div>

		<button
			onclick={(e) => {
				e.stopPropagation();
				nextImage();
			}}
			class="btn absolute right-4 btn-circle text-white btn-ghost"
			aria-label="Next image"
		>
			<svg
				xmlns="http://www.w3.org/2000/svg"
				class="h-8 w-8"
				fill="none"
				viewBox="0 0 24 24"
				stroke="currentColor"
			>
				<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
			</svg>
		</button>

		<div class="absolute bottom-4 left-1/2 -translate-x-1/2 text-white">
			{currentImageIndex + 1} / {data.items.length}
		</div>
	</div>
{/if}
