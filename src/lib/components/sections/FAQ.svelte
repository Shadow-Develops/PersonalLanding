<script>
	let { data } = $props();
</script>

<section id="faq" class="px-4 py-16">
	<div class="mx-auto max-w-3xl">
		<h2 class="mb-12 text-center text-3xl font-bold">{data.title}</h2>
		<div class="space-y-4">
			{#each data.items as item, i}
				<div class="collapse-arrow collapse bg-base-100 shadow">
					<input type="radio" name="faq-accordion" checked={i === 0} />
					<div class="collapse-title text-lg font-medium">
						{item.question}
					</div>
					<div class="collapse-content">
						<p class="text-base-content/70">{item.answer}</p>
					</div>
				</div>
			{/each}
		</div>
	</div>
</section>
