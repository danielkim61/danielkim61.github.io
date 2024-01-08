<script lang="ts">
	import TikTokEmbed from '$lib/TikTokEmbed.svelte';
	import { Modal } from '@sveltestrap/sveltestrap';
	import { IconPlayerPlay } from '@tabler/icons-svelte';

	export let url: string;
	export let img: string;
	export let views: string = '';
	let classes: String = '';
	export { classes as class };
	export let story = false;

	var isOpen = false;
	function toggle() {
		isOpen = !isOpen;
	}
</script>

<button class="btn {classes}" class:story on:click={toggle}>
	<img
		class:story
		class:large={!story}
		class="img-fluid w-100"
		src={img}
		alt="TikTok Video Thumbnail"
	/>
	{#if !story}
		<div class="play-info p-2 d-flex align-items-center">
			<IconPlayerPlay size={16} stroke={3} class="me-1" />
			{views}
		</div>
	{/if}
</button>

<Modal body {isOpen} {toggle}>
	<TikTokEmbed {url} />
</Modal>

<style>
	.btn {
		margin: 0;
		padding: 0;
		position: relative;
		border: none;
		margin-bottom: 0.25rem;
	}
	.btn :not(.story) {
		margin-right: 1rem;
		margin-bottom: 1rem;
	}
	img {
		max-width: 400px;
	}
	img.story {
		aspect-ratio: 1;
		object-fit: cover;
		border-radius: 50%;
		outline: 1px solid #00000020;
		outline-offset: -1px;
	}
	img.large {
		aspect-ratio: 0.8;
		object-fit: cover;
	}
	.play-info {
		position: absolute;
		bottom: 0;
		left: 0;
		right: 0;
		color: white;
		background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.5));
		font-weight: 500;
	}
</style>
