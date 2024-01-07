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

<button class="btn {classes}" on:click={toggle}>
	<img class:story class="img-fluid w-100" src={img} alt="TikTok Video Thumbnail" />
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
		padding-right: 0.25rem;
		padding-bottom: 0.25rem;
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
</style>
