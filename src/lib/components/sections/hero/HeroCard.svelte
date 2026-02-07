<script>
	let { data } = $props();
</script>

<section class="hero flex min-h-[70vh] items-center justify-center px-4">
	<div class="card w-full max-w-lg bg-base-200/50 shadow-xl backdrop-blur-sm">
		<div class="card-body items-center text-center">
			{#if data.showAvatar && data.avatar}
				<div class="avatar mb-4">
					<div class="h-24 w-24 rounded-full ring ring-primary ring-offset-2 ring-offset-base-200">
						<img src={data.avatar} alt={data.name} />
					</div>
				</div>
			{/if}
			<h1
				class="card-title bg-linear-to-r from-primary to-secondary bg-clip-text text-4xl font-bold text-transparent md:text-5xl"
			>
				{data.name}
			</h1>
			{#if data.tagline}
				<p class="mt-2 text-base-content/70">
					{data.tagline}
				</p>
			{/if}
		</div>
	</div>
</section>
