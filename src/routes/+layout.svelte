<script>
	import Menu from '$lib/Menu.svelte';
	import { page } from '$app/stores';
	import CreativeHighlights from '$lib/CreativeHighlights.svelte';
</script>

<div class="container">
	<div class="d-flex">
		<Menu />
		<div class="col pt-4">
			<slot />
		</div>
		{#if $page.url.pathname == '/'}
			<CreativeHighlights />
		{/if}
	</div>
</div>
