<script>
	import Menu from '$lib/Menu.svelte';
	import { page } from '$app/stores';
	import CreativeHighlights from '$lib/CreativeHighlights.svelte';
	import { base } from '$app/paths';
</script>

<div class="container">
	<div class="d-flex">
		<Menu />
		<div class="col pt-4">
			<slot />
		</div>
		{#if $page.url.pathname == `${base}/`}
			<CreativeHighlights />
		{/if}
	</div>
</div>
