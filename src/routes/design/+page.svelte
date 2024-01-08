<script lang="ts">
	import Gallery from '$lib/Gallery.svelte';
	import { Col, Row } from '@sveltestrap/sveltestrap';
	import { base } from '$app/paths';

	var isOpen = false;
	var index = 0;
	function toggle() {
		isOpen = !isOpen;
	}
	function openGallery(i: number) {
		isOpen = true;
		index = i;
	}

	let images = [
		{ src: `${base}/design/duke.jpg`, caption: 'Duke University' },
		{ src: `${base}/design/unc.jpg`, caption: 'University of North Carolina at Chapel Hill' },
		{ src: `${base}/design/stanford.jpg`, caption: 'Stanford University' },
		{ src: `${base}/design/la.jpg`, caption: 'UCLA' },
		{ src: `${base}/design/cameron.jpg`, caption: 'Cameron Indoor Stadium, Duke University' },
		{ src: `${base}/design/ucb.jpg`, caption: 'UC Berkeley' },
		{ src: `${base}/design/iu.jpg`, caption: 'Indiana University' },
		{ src: `${base}/design/uiuc.jpg`, caption: 'University of Illinois Urbana-Champaign' },
		{ src: `${base}/design/gatech_2.jpg`, caption: 'Georgia Tech' },
		{ src: `${base}/design/gatech.jpg`, caption: 'Georgia Tech' },
		{ src: `${base}/design/love.jpg`, caption: 'University of Pennsylvania' },
		{ src: `${base}/design/ohio.jpg`, caption: 'Ohio State University' },
		{ src: `${base}/design/philly_2.jpg`, caption: 'Philadelphia, PA' },
		{ src: `${base}/design/philly.jpg`, caption: 'Philadelphia, PA' },
		{
			src: `${base}/design/upenn.jpg`,
			caption: 'Wharton School of Business, University of Pennsylvania'
		}
	];
</script>

<Gallery {isOpen} {toggle} bind:index images={images.map((i) => i.src)} />

<Row class="ms-5 gy-3 gx-3">
	{#each images as img, i}
		<Col md="6">
			<button
				class="btn p-0 m-0 position-relative"
				style:border="none"
				on:click={() => {
					openGallery(i);
				}}
			>
				<img src={img.src} class="square w-100 h-100" alt="Graphic Design Gallery" />
				<div class="w-100 h-100 position-absolute text-center hover d-flex align-items-center">
					<div style:font-size="20px" class="text-white m-auto px-4">
						{img.caption}
					</div>
				</div>
			</button>
		</Col>
	{/each}
</Row>

<style>
	img.square {
		aspect-ratio: 1 !important;
		object-fit: cover;
		width: 80%;
		height: 80%;
	}

	button .hover {
		background: rgba(64, 64, 64, 0.4);
		top: 0;
		left: 0;
		opacity: 0;
		transition: opacity 0.5s ease;
		font-weight: 500;
	}

	button:hover .hover {
		opacity: 1;
	}
</style>
