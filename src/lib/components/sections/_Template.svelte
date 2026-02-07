<!--
============================================================
SECTION TEMPLATE
============================================================

This is a template for creating custom sections. To use it:

1. Copy this file and rename it (e.g., MySection.svelte)
	- The filename becomes the config key (lowercase first letter)
	- Example: MySection.svelte -> "mySection" in config

2. Add configuration in config.json under "sections" array:
	{
		"type": "mySection",
		"enabled": true,
		"title": "My Section",
		"yourCustom": "data"
	}

	The position in the array determines the display order.
	You can add the same section type multiple times with different settings!

That's it! The section will be automatically discovered and rendered.

============================================================
NAMING CONVENTION
============================================================

- Filename: PascalCase (e.g., MySection.svelte, CustomHero.svelte)
- Config key: camelCase (e.g., mySection, customHero)
- Files starting with _ are ignored (like this template)

============================================================
STYLING TIPS
============================================================

- Use Tailwind CSS classes for styling
- DaisyUI components available: https://daisyui.com/components/
- Alternate sections with bg-base-200/50 for visual separation
- Use max-w-* classes to constrain content width
- Common patterns:
- py-16 px-4       : Standard section padding
- max-w-4xl mx-auto: Centered content container
- text-center      : Centered text
- text-base-content/70: Muted text color

============================================================
THEME COLORS (from your DaisyUI config)
============================================================

- primary   : Main accent color (buttons, links)
- secondary : Secondary accent
- accent    : Highlight color
- base-100  : Background
- base-200  : Slightly darker background
- base-content: Text color

============================================================
-->

<script>
	// Props passed from the parent component
	// The 'data' prop contains everything from config.json for this section
	let { data } = $props();

	// You can add reactive state using Svelte 5 runes
	// let count = $state(0);

	// You can add derived values
	// let doubled = $derived(count * 2);

	// Helper functions for your section
	// function handleClick() {
	//   count++;
	// }
</script>

<!--
  Section wrapper with:
  - id: For navigation/anchor links
  - py-16 px-4: Vertical and horizontal padding
  - bg-base-200/50: Optional background tint (remove for plain)
-->
<section id="custom" class="bg-base-200/50 px-4 py-16">
	<!-- Content container - adjust max-w-* for desired width -->
	<div class="mx-auto max-w-4xl">
		<!-- Section title -->
		{#if data.title}
			<h2 class="mb-12 text-center text-3xl font-bold">{data.title}</h2>
		{/if}

		<!-- Your content goes here -->
		<div class="text-center">
			<p class="text-base-content/70">
				This is a template section. Replace this content with your own.
			</p>
		</div>

		<!-- Example: Iterating over items from config -->
		<!--
		{#if data.items}
			<div class="grid gap-6 md:grid-cols-2 lg:grid-cols-3">
				{#each data.items as item}
					<div class="card bg-base-100 shadow-lg">
						<div class="card-body">
							<h3 class="card-title">{item.title}</h3>
							<p>{item.description}</p>
						</div>
					</div>
				{/each}
			</div>
		{/if}
		-->

		<!-- Example: Conditional rendering -->
		<!--
		{#if data.showButton}
			<button class="btn btn-primary mt-8">Click Me</button>
		{/if}
		-->

		<!-- Example: Using DaisyUI components -->
		<!--
		<div class="alert alert-info mt-8">
			<span>This is an info alert</span>
		</div>
		-->
	</div>
</section>

<style>
	/*
		Add component-scoped styles here if needed.
		Prefer Tailwind classes when possible.
	*/
</style>
