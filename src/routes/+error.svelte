<script>
	import { page } from '$app/stores';
	import { base } from '$app/paths';
	import { fade, scale } from 'svelte/transition';
</script>

<svelte:head>
	<title>{$page.status} | Error</title>
</svelte:head>

<section class="flex min-h-screen items-center justify-center bg-base-100 px-4">
	<div class="text-center" in:fade={{ duration: 300 }}>
		<div class="mb-8" in:scale={{ duration: 400, delay: 100 }}>
			<span
				class="bg-linear-to-r from-error to-warning bg-clip-text text-[9rem] leading-none font-black text-transparent md:text-[12rem]"
			>
				{$page.status}
			</span>
		</div>

		<h1 class="mb-4 text-3xl font-bold text-base-content md:text-4xl">
			{#if $page.status === 404}
				Page Not Found
			{:else if $page.status === 500}
				Server Error
			{:else}
				Something Went Wrong
			{/if}
		</h1>

		<p class="mx-auto mb-8 max-w-xl text-lg text-base-content/60">
			{#if $page.error?.message && $page.error?.message !== 'Not Found'}
				{$page.error.message}
			{:else if $page.status === 404}
				The page you're looking for doesn't exist or has been moved.
			{:else}
				An unexpected error occurred. Please try again later.
			{/if}
		</p>

		<div class="flex flex-col items-center justify-center gap-4 sm:flex-row">
			<a href="{base}/" class="btn gap-2 transition-transform btn-lg btn-primary hover:scale-105">
				<svg
					xmlns="http://www.w3.org/2000/svg"
					class="h-5 w-5"
					viewBox="0 0 20 20"
					fill="currentColor"
				>
					<path
						d="M10.707 2.293a1 1 0 00-1.414 0l-7 7a1 1 0 001.414 1.414L4 10.414V17a1 1 0 001 1h2a1 1 0 001-1v-2a1 1 0 011-1h2a1 1 0 011 1v2a1 1 0 001 1h2a1 1 0 001-1v-6.586l.293.293a1 1 0 001.414-1.414l-7-7z"
					/>
				</svg>
				Back to Home
			</a>
			<button
				onclick={() => history.back()}
				class="btn gap-2 transition-transform btn-outline btn-lg hover:scale-105"
			>
				<svg
					xmlns="http://www.w3.org/2000/svg"
					class="h-5 w-5"
					viewBox="0 0 20 20"
					fill="currentColor"
				>
					<path
						fill-rule="evenodd"
						d="M9.707 16.707a1 1 0 01-1.414 0l-6-6a1 1 0 010-1.414l6-6a1 1 0 011.414 1.414L5.414 9H17a1 1 0 110 2H5.414l4.293 4.293a1 1 0 010 1.414z"
						clip-rule="evenodd"
					/>
				</svg>
				Go Back
			</button>
		</div>
	</div>
</section>
