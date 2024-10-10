<script lang="ts">
	import { browser } from '$app/environment';
	import { page } from '$app/stores';
	import { webVitals } from '$lib/vitals';
	import '../app.postcss';
	import './styles.css';
	import pigEmoji from '$lib/images/pig-emoji.png'
	import pigSplash from '$lib/images/porcamento-transparent.png'

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
			<img class="app-icon" src={pigEmoji} alt="pig emoji">
		</svelte:fragment>
		<h3 class="h3">Porca Mentos</h3>
		<svelte:fragment slot="trail">
			<i class="bi bi-gear"></i>
		</svelte:fragment>
	</AppBar>
	<main class="container py-8 ">
		<div class="grid grid-cols-2 gap-4">

			
			<img src={pigSplash} alt="">
			<div class="flex flex-col justify-center gap-4">
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

	.app-icon {
		max-height: 40px;
	}
</style>
