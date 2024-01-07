<script lang="ts">
	import { Row, Col } from '@sveltestrap/sveltestrap';
	import DanielAvatar from './DanielAvatar.svelte';
	import Gallery from './Gallery.svelte';
	import Post from './Post.svelte';

	var isOpen = false;
	var index = 0;
	function toggle() {
		isOpen = !isOpen;
	}
	function openGallery(i: number) {
		isOpen = true;
		index = i;
	}

	export let images: string[];
	export let maxImages = 5;
	export let caption: string;
</script>

<Gallery {isOpen} {toggle} bind:index {images} />

<Post>
	<Row class="g-1 gy-1">
		{#each Array(Math.min(images.length, maxImages)) as _, i}
			<Col md={i <= 1 ? 6 : 4}>
				<button
					class="position-relative btn btn-link p-0 border-none"
					on:click={() => {
						openGallery(i);
					}}
				>
					<img class="img-fluid square" src={images[i]} alt="Gallery" />
					{#if i == maxImages - 1 && images.length > maxImages}
						<div
							class="position-absolute fixed-top fixed-bottom w-100 text-center d-grid align-items-center text-white"
							style:background="rgba(0, 0, 0, .5)"
							style:z-index="10"
							style:font-size="28px"
						>
							+{images.length - 5}
						</div>
					{/if}
				</button>
			</Col>
		{/each}
		<Col class="graybox p-2">
			<DanielAvatar class="d-inline-block align-top" />
			<strong>Daniel</strong>
			{caption}
		</Col>
	</Row>
</Post>

<style>
	img.square {
		aspect-ratio: 1 !important;
		object-fit: cover;
	}
</style>
