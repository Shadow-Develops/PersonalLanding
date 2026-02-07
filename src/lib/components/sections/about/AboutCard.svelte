<script>
	let { data } = $props();
</script>

<section id="about" class="px-4 py-16">
	<div class="mx-auto max-w-4xl">
		<h2 class="mb-12 text-center text-3xl font-bold">{data.title}</h2>
		<div class="card bg-base-200/50 shadow-xl">
			<div class="card-body items-center text-center">
				{#if data.avatar}
					<div class="avatar mb-6">
						<div class="w-32 rounded-full ring ring-primary ring-offset-4 ring-offset-base-100">
							<img src={data.avatar} alt={data.title} />
						</div>
					</div>
				{/if}
				<p class="max-w-2xl text-lg leading-relaxed text-base-content/80">
					{data.content}
				</p>
				{#if data.skills && data.skills.length > 0}
					<div class="mt-8 card-actions">
						<div class="flex flex-wrap justify-center gap-2">
							{#each data.skills as skill}
								<div class="badge badge-outline badge-lg">{skill}</div>
							{/each}
						</div>
					</div>
				{/if}
			</div>
		</div>
	</div>
</section>
