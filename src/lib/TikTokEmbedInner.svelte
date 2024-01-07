<script lang="ts">
	import IntersectionObserver from 'svelte-intersection-observer';

	let element: HTMLElement;

	function loadEmbed() {
		console.log('loading');
		const tiktoksOnPage = Array.from(element.querySelectorAll('blockquote.tiktok-embed'));
		// @ts-ignore
		if (typeof window.tiktokEmbed !== 'undefined' && tiktoksOnPage.length) {
			// @ts-ignore
			window.tiktokEmbed.lib.render(tiktoksOnPage);
		}
	}
</script>

<IntersectionObserver {element} once on:intersect={loadEmbed}>
	<div bind:this={element}><slot /></div>
</IntersectionObserver>
