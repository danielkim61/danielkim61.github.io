<script lang="ts">
	import TikTokEmbedInner from './TikTokEmbedInner.svelte';

	export let url: string;

	async function fetchEmbedCode() {
		let response = await fetch(`https://www.tiktok.com/oembed?url=${url}`);
		if (response.ok) {
			let data = await response.json();
			if (data.html) {
				return data.html;
			}
			return '';
		}
	}
</script>

{#await fetchEmbedCode() then html}
	<TikTokEmbedInner>
		{@html html}
	</TikTokEmbedInner>
{/await}
