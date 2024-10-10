<script lang="ts">
	import { browser } from '$app/environment';
	import { page } from '$app/stores';
	import { webVitals } from '$lib/vitals';
	import '../app.postcss';
	import './styles.css';

	import {
		AppBar,
		FileDropzone,
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
	<AppBar>
		<svelte:fragment slot="lead">
			<img src="../static/favicon.png" alt="">
		</svelte:fragment>
		(title)
		<svelte:fragment slot="trail">(actions)</svelte:fragment>
	</AppBar>
	<main class="container py-8 ">
		<div class="grid grid-cols-2 gap-4">

			<div>teste</div>
			<div class="flex flex-col gap-4">
				<FileDropzone name="alu-file" />
				<FileDropzone name="vid-file" />
			</div>
		</div>
	</main>
	<slot />
</div>

<style>
	.app {
		display: flex;
		flex-direction: column;
		min-height: 100vh;
	}
</style>
