<script>
	let { data } = $props();
</script>

<section id="links" class="px-4 py-16">
	<div class="mx-auto max-w-2xl">
		<h2 class="mb-12 text-center text-3xl font-bold">{data.title}</h2>
		<div class="flex flex-col items-center gap-2">
			{#each data.items as link}
				<a
					href={link.url}
					target="_blank"
					rel="noopener noreferrer"
					class="group relative text-lg font-light transition-colors hover:text-primary"
				>
					{link.name}
					<span
						class="absolute -bottom-1 left-0 h-px w-0 bg-primary transition-all group-hover:w-full"
					></span>
				</a>
			{/each}
		</div>
	</div>
</section>
