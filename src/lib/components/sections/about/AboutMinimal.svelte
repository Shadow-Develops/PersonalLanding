<script>
	let { data } = $props();
</script>

<section id="about" class="px-4 py-16">
	<div class="mx-auto max-w-2xl">
		<h2 class="mb-8 text-4xl font-light tracking-tight">{data.title}</h2>
		<p class="text-xl leading-relaxed text-base-content/70">
			{data.content}
		</p>
		{#if data.skills && data.skills.length > 0}
			<div class="mt-12 flex flex-wrap gap-4">
				{#each data.skills as skill}
					<span class="text-base-content/60">{skill}</span>
				{/each}
			</div>
		{/if}
	</div>
</section>
