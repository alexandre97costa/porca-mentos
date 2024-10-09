<script lang="ts">
	import { browser } from '$app/environment';
	import { page } from '$app/stores';
	import { webVitals } from '$lib/vitals';
	import '../app.postcss';
	import './styles.css';

	import {
		AppBar,
		AppShell,
		LightSwitch,
		storePopup,
		popup,

		Avatar

	} from '@skeletonlabs/skeleton';

	/** @type {import('./$types').LayoutServerData} */
	export let data;

	$: if (browser && data?.analyticsId) {
		webVitals({
			path: $page.url.pathname,
			params: $page.params,
			analyticsId: data.analyticsId
		});
	}
</script>

<div class="app">
	<main>
		<slot />
	</main>
</div>
<p>teste</p>
<button type="button" class="btn-icon variant-filled-primary">(icon)</button>
<button type="button" class="btn variant-filled-primary">Button</button>
<button type="button" class="btn variant-filled-primary">
	<i class="bi bi-cart"></i>
	<span>(icon)</span>
	<span>Button</span>
</button>

<style>
	.app {
		display: flex;
		flex-direction: column;
		min-height: 50vh;
	}

	main {
		flex: 1;
		display: flex;
		flex-direction: column;
		padding: 1rem;
		width: 100%;
		max-width: 64rem;
		margin: 0 auto;
		box-sizing: border-box;
	}

</style>
