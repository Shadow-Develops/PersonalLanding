<script>
	let { data } = $props();

	let formState = $state('idle');
	let formError = $state('');

	const buttonHref = $derived(
		data.button?.type === 'email' ? `mailto:${data.button.value}` : data.button?.value
	);

	async function handleSubmit(event) {
		event.preventDefault();
		formState = 'submitting';
		formError = '';

		const form = event.target;
		const formData = new FormData(form);

		try {
			const response = await fetch(`https://formsubmit.co/ajax/${data.form.email}`, {
				method: 'POST',
				body: formData,
				headers: {
					Accept: 'application/json'
				}
			});

			if (response.ok) {
				formState = 'success';
				form.reset();
			} else {
				throw new Error('Form submission failed');
			}
		} catch {
			formState = 'error';
			formError = 'Something went wrong. Please try again.';
		}
	}
</script>

<section id="contact" class="bg-base-200/50 px-4 py-16">
	<div class="mx-auto max-w-2xl text-center">
		<h2 class="mb-6 text-3xl font-bold">{data.title}</h2>
		{#if data.description}
			<p class="mb-8 text-lg text-base-content/70">{data.description}</p>
		{/if}

		{#if data.form?.enabled}
			<div class="card bg-base-100 shadow-lg">
				<div class="card-body">
					{#if formState === 'success'}
						<div class="alert alert-success">
							<svg
								xmlns="http://www.w3.org/2000/svg"
								class="h-6 w-6 shrink-0 stroke-current"
								fill="none"
								viewBox="0 0 24 24"
								><path
									stroke-linecap="round"
									stroke-linejoin="round"
									stroke-width="2"
									d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"
								/></svg
							>
							<span>{data.form.successMessage}</span>
						</div>
					{:else}
						<form onsubmit={handleSubmit} class="space-y-4">
							<input type="hidden" name="_subject" value={data.form.subject} />
							<input type="hidden" name="_captcha" value="false" />

							<div class="form-control">
								<input
									type="text"
									name="name"
									placeholder={data.form.namePlaceholder}
									class="input-bordered input w-full"
									required
								/>
							</div>

							<div class="form-control">
								<input
									type="email"
									name="email"
									placeholder={data.form.emailPlaceholder}
									class="input-bordered input w-full"
									required
								/>
							</div>

							<div class="form-control">
								<textarea
									name="message"
									placeholder={data.form.messagePlaceholder}
									class="textarea-bordered textarea h-32 w-full"
									required
								></textarea>
							</div>

							{#if formState === 'error'}
								<div class="alert alert-error">
									<span>{formError}</span>
								</div>
							{/if}

							<button
								type="submit"
								class="btn w-full btn-primary"
								disabled={formState === 'submitting'}
							>
								{#if formState === 'submitting'}
									<span class="loading loading-sm loading-spinner"></span>
									Sending...
								{:else}
									{data.form.submitText}
								{/if}
							</button>
						</form>
					{/if}
				</div>
			</div>
		{/if}

		{#if data.button && data.button?.enabled}
			<a
				href={buttonHref}
				class="btn mt-6 gap-2 btn-lg btn-primary"
				target={data.button.type === 'link' ? '_blank' : undefined}
				rel={data.button.type === 'link' ? 'noopener noreferrer' : undefined}
			>
				{#if data.button.type === 'email'}
					<svg
						xmlns="http://www.w3.org/2000/svg"
						width="20"
						height="20"
						viewBox="0 0 24 24"
						fill="none"
						stroke="currentColor"
						stroke-width="2"
						stroke-linecap="round"
						stroke-linejoin="round"
						><rect width="20" height="16" x="2" y="4" rx="2" /><path
							d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"
						/></svg
					>
				{:else}
					<svg
						xmlns="http://www.w3.org/2000/svg"
						width="20"
						height="20"
						viewBox="0 0 24 24"
						fill="none"
						stroke="currentColor"
						stroke-width="2"
						stroke-linecap="round"
						stroke-linejoin="round"
						><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6" /><polyline
							points="15 3 21 3 21 9"
						/><line x1="10" x2="21" y1="14" y2="3" /></svg
					>
				{/if}
				{data.button.text}
			</a>
		{/if}
	</div>
</section>
