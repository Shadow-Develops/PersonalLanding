<script>
	let { data } = $props();
</script>

<section class="hero flex min-h-[60vh] items-center justify-center">
	<div class="hero-content flex-col text-center">
		<h1 class="text-5xl font-light tracking-tight text-base-content md:text-7xl">
			{data.name}
		</h1>
		{#if data.tagline}
			<p class="mt-6 max-w-md text-lg text-base-content/60">
				{data.tagline}
			</p>
		{/if}
	</div>
</section>
