<script>
	let { data } = $props();
</script>

<section id="about" class="px-4 py-16">
	<div class="mx-auto max-w-3xl">
		<h2 class="mb-8 text-center text-3xl font-bold">{data.title}</h2>
		<p class="text-center text-lg leading-relaxed text-base-content/80">
			{data.content}
		</p>
		{#if data.skills && data.skills.length > 0}
			<div class="mt-8 flex flex-wrap justify-center gap-2">
				{#each data.skills as skill}
					<span class="badge badge-lg badge-primary">{skill}</span>
				{/each}
			</div>
		{/if}
	</div>
</section>
