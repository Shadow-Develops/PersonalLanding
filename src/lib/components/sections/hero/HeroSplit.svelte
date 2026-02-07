<script>
	let { data } = $props();
</script>

<section class="hero min-h-[70vh]">
	<div class="hero-content flex-col gap-8 lg:flex-row-reverse lg:gap-16">
		{#if data.showAvatar && data.avatar}
			<div class="avatar">
				<div class="w-48 rounded-xl shadow-2xl lg:w-72">
					<img src={data.avatar} alt={data.name} />
				</div>
			</div>
		{/if}
		<div class="text-center lg:text-left">
			<h1
				class="bg-linear-to-r from-primary to-secondary bg-clip-text text-5xl font-bold text-transparent md:text-6xl"
			>
				{data.name}
			</h1>
			{#if data.tagline}
				<p class="mt-6 max-w-lg text-xl text-base-content/70 md:text-2xl">
					{data.tagline}
				</p>
			{/if}
		</div>
	</div>
</section>
