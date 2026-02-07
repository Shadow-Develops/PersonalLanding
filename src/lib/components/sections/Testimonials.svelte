<script>
	let { data } = $props();
</script>

<section id="testimonials" class="px-4 py-16">
	<div class="mx-auto max-w-4xl">
		<h2 class="mb-12 text-center text-3xl font-bold">{data.title}</h2>
		<div class="grid gap-6 md:grid-cols-2">
			{#each data.items as testimonial}
				<div class="card bg-base-100 shadow-lg">
					<div class="card-body">
						<blockquote class="text-base-content/80 italic">
							"{testimonial.quote}"
						</blockquote>
						<div class="mt-4 flex items-center gap-3">
							{#if testimonial.avatar}
								<div class="avatar">
									<div class="h-10 w-10 rounded-full">
										<img src={testimonial.avatar} alt={testimonial.name} />
									</div>
								</div>
							{/if}
							<div>
								<div class="font-semibold">{testimonial.name}</div>
								{#if testimonial.role}
									<div class="text-sm text-base-content/60">{testimonial.role}</div>
								{/if}
							</div>
						</div>
					</div>
				</div>
			{/each}
		</div>
	</div>
</section>
