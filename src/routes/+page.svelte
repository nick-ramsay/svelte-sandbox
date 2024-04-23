<script lang="ts">
	import Counter from './Counter.svelte';
	import welcome from '$lib/images/svelte-welcome.webp';
	import welcome_fallback from '$lib/images/svelte-welcome.png';

	import { datadogRum } from '@datadog/browser-rum';

	datadogRum.init({
    	applicationId: 'bfb434f5-4dcf-4fa4-9a84-f7e622c6be78',
    	clientToken: 'pub067ef0f19bdd42b4b15c7e3a1f89d1f4',
    	// `site` refers to the Datadog site parameter of your organization
    	// see https://docs.datadoghq.com/getting_started/site/
    	site: 'datadoghq.com',
    	service: 'svelte-sandbox',
    	env: 'staging',
    	// Specify a version number to identify the deployed version of your application in Datadog
    	// version: '1.0.0', 
    	sessionSampleRate: 100,
    	sessionReplaySampleRate: 100,
    	trackUserInteractions: true,
    	trackResources: true,
    	trackLongTasks: true,
    	defaultPrivacyLevel: 'mask-user-input',
});
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section>
	<h1>
		<span class="welcome">
			<picture>
				<source srcset={welcome} type="image/webp" />
				<img src={welcome_fallback} alt="Welcome" />
			</picture>
		</span>

		to your new<br />SvelteKit app
	</h1>

	<h2>
		try editing <strong>src/routes/+page.svelte</strong>
	</h2>

	<Counter />
</section>
<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
	}

	h1 {
		width: 100%;
	}

	.welcome {
		display: block;
		position: relative;
		width: 100%;
		height: 0;
		padding: 0 0 calc(100% * 495 / 2048) 0;
	}

	.welcome img {
		position: absolute;
		width: 100%;
		height: 100%;
		top: 0;
		display: block;
	}
</style>
