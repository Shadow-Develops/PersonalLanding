<script>
	let { data } = $props();
</script>

<section class="hero flex min-h-[70vh] items-center justify-center">
	<div class="hero-content flex-col text-center">
		{#if data.showAvatar && data.avatar}
			<div class="avatar mb-6">
				<div class="h-32 w-32 rounded-full ring ring-primary ring-offset-2 ring-offset-base-100">
					<img src={data.avatar} alt={data.name} />
				</div>
			</div>
		{/if}
		<h1
			class="bg-linear-to-r from-primary to-secondary bg-clip-text text-5xl font-bold text-transparent md:text-6xl"
		>
			{data.name}
		</h1>
		{#if data.tagline}
			<p class="mt-4 max-w-xl text-xl text-base-content/70 md:text-2xl">
				{data.tagline}
			</p>
		{/if}
	</div>
</section>
