<script lang="ts">
	import TikTokEmbed from '$lib/TikTokEmbed.svelte';
	import { Modal } from '@sveltestrap/sveltestrap';

	export let url: string;
	export let img: string;
	let classes: String = '';
	export { classes as class };
	export let story = false;

	var isOpen = false;
	function toggle() {
		isOpen = !isOpen;
	}
</script>

<button class="btn btn-link {classes}" on:click={toggle}>
	<img class:story class="img-fluid" src={img} alt="TikTok Video Thumbnail" />
	<div class="story-border" />
</button>

<Modal body {isOpen} {toggle}>
	<TikTokEmbed {url} />
</Modal>

<style>
	.btn {
		margin: 0;
		padding: 0;
		position: relative;
		border: 0;
		padding-right: 0.25rem;
		padding-bottom: 0.25rem;
	}
	img {
		width: 400px;
	}
	img.story {
		aspect-ratio: 1;
		object-fit: cover;
		border-radius: 50%;
	}
	.story-border {
		position: absolute;
		left: 0;
		top: 0;
		right: 0;
		bottom: 0;
		border: 1px solid #00000020;
		border-radius: 50%;
		z-index: 10;
	}
</style>
