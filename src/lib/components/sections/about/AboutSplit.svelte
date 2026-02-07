<script>
	let { data } = $props();
</script>

<section id="about" class="bg-base-200/50 px-4 py-16">
	<div class="mx-auto max-w-6xl">
		<h2 class="mb-12 text-center text-3xl font-bold">{data.title}</h2>
		<div class="grid items-center gap-12 md:grid-cols-2">
			<div class="order-2 md:order-1">
				<p class="text-lg leading-relaxed text-base-content/80">
					{data.content}
				</p>
				{#if data.skills && data.skills.length > 0}
					<div class="mt-8 flex flex-wrap gap-2">
						{#each data.skills as skill}
							<span class="badge badge-lg badge-primary">{skill}</span>
						{/each}
					</div>
				{/if}
			</div>
			<div class="order-1 md:order-2">
				{#if data.image}
					<img src={data.image} alt={data.title} class="w-full rounded-lg shadow-xl" />
				{:else if data.avatar}
					<div class="flex justify-center">
						<div class="avatar">
							<div class="w-64 rounded-full ring ring-primary ring-offset-2 ring-offset-base-100">
								<img src={data.avatar} alt={data.title} />
							</div>
						</div>
					</div>
				{:else}
					<div
						class="flex aspect-square items-center justify-center rounded-lg bg-linear-to-br from-primary to-secondary"
					>
						<span class="text-9xl font-bold text-white opacity-20">?</span>
					</div>
				{/if}
			</div>
		</div>
	</div>
</section>
