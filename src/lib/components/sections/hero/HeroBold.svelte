<script>
	let { data } = $props();
</script>

<section class="relative hero min-h-[80vh] overflow-hidden">
	<div
		class="absolute inset-0 bg-linear-to-br from-primary/10 via-transparent to-secondary/10"
	></div>
	<div class="relative hero-content z-10 flex-col text-center">
		{#if data.showAvatar && data.avatar}
			<div class="avatar mb-8">
				<div
					class="h-40 w-40 rounded-full ring-4 ring-primary ring-offset-4 ring-offset-base-100 md:h-48 md:w-48"
				>
					<img src={data.avatar} alt={data.name} />
				</div>
			</div>
		{/if}
		<h1
			class="bg-linear-to-r from-primary via-secondary to-accent bg-clip-text text-6xl font-black tracking-wider text-transparent uppercase md:text-8xl"
		>
			{data.name}
		</h1>
		{#if data.tagline}
			<p class="mt-6 max-w-2xl text-xl font-medium text-base-content/80 md:text-3xl">
				{data.tagline}
			</p>
		{/if}
	</div>
</section>
