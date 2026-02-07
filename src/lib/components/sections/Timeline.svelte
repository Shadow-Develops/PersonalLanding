<script>
	let { data } = $props();
</script>

<section id="timeline" class="bg-base-200/50 px-4 py-16">
	<div class="mx-auto max-w-3xl">
		<h2 class="mb-12 text-center text-3xl font-bold">{data.title}</h2>
		<ul class="timeline timeline-vertical timeline-snap-icon">
			{#each data.items as item, i}
				<li>
					{#if i > 0}
						<hr class="bg-primary" />
					{/if}
					<div class="timeline-middle">
						<svg
							xmlns="http://www.w3.org/2000/svg"
							viewBox="0 0 20 20"
							fill="currentColor"
							class="h-5 w-5 text-primary"
						>
							<path
								fill-rule="evenodd"
								d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.857-9.809a.75.75 0 00-1.214-.882l-3.483 4.79-1.88-1.88a.75.75 0 10-1.06 1.061l2.5 2.5a.75.75 0 001.137-.089l4-5.5z"
								clip-rule="evenodd"
							/>
						</svg>
					</div>
					<div
						class="timeline-{i % 2 === 0 ? 'start' : 'end'} {i % 2 === 0
							? 'md:text-end'
							: ''} mb-10"
					>
						<time class="font-mono text-sm text-base-content/60">{item.date}</time>
						<div class="text-lg font-bold">{item.title}</div>
						{#if item.subtitle}
							<div class="text-sm text-primary">{item.subtitle}</div>
						{/if}
						{#if item.description}
							<p class="mt-1 text-base-content/70">{item.description}</p>
						{/if}
					</div>
					{#if i < data.items.length - 1}
						<hr class="bg-primary" />
					{/if}
				</li>
			{/each}
		</ul>
	</div>
</section>
