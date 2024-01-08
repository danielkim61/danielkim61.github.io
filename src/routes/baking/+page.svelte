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

	let bakingImages = [
		{ src: `${base}/cookies/xmas3.jpg`, caption: 'Classic Christmas Cookie Order' },
		{ src: `${base}/cakes/rose.jpg`, caption: 'Garden Party Cake' },
		{ src: `${base}/cakes/unc.jpg`, caption: 'UNC Chapel Hill Graduation Cake' },
		{ src: `${base}/cookies/xmas1.jpg`, caption: 'Modern Christmas Cookie Order' },
		{ src: `${base}/cookies/dog.jpg`, caption: 'BarkBox™ Cookie Order' },
		{ src: `${base}/cakes/guitar.jpg`, caption: 'Rock & Roll Cake Order' },
		{ src: `${base}/cookies/duke.jpg`, caption: 'Duke University Winter Event' },
		{ src: `${base}/cookies/newyork.jpg`, caption: "New Year's Eve Wedding Cookie Order" },
		{ src: `${base}/cakes/wedding.jpg`, caption: 'Three-Tier Fondant Wedding Cake' },
		{ src: `${base}/cookies/cvs1.jpg`, caption: 'CVS Health Philadelphia Corporate Event' },
		{ src: `${base}/cookies/xmas2.jpg`, caption: 'Holiday Cookie Order' },
		{ src: `${base}/cookies/easter.jpg`, caption: 'Easter Tea Party Cookie Order' },
		{ src: `${base}/cookies/cvs2.jpg`, caption: 'CVS Health NYC Corporate Event' },
		{ src: `${base}/cakes/spiderman.jpg`, caption: 'Spiderman-Themed Birthday Cake' },
		{ src: `${base}/cookies/alabama.jpg`, caption: 'University of Alabama Cookie Order' },
		{ src: `${base}/cookies/disco.jpg`, caption: 'Disco Bridal Shower Cookie Order' },
		{ src: `${base}/cakes/meg.jpg`, caption: 'Birthday Cake Order' },
		{ src: `${base}/cakes/mom.jpg`, caption: 'Floral Birthday Cake' },
		{ src: `${base}/cakes/sophie.jpg`, caption: 'Princess-Themed Birthday Cake' },
		{ src: `${base}/cakes/chocolate.jpg`, caption: 'Chocolate Birthday Cake' },
		{ src: `${base}/cakes/baby_princess.jpg`, caption: 'Baby Princess Cake' },
		{ src: `${base}/cakes/kim.jpg`, caption: 'Spring Birthday Cake' },
		{ src: `${base}/cakes/m.jpg`, caption: 'Gatsby-Themed Three-Tier Birthday Cake' },
		{ src: `${base}/cakes/table.jpg`, caption: 'UNC Chapel Hill Graduation Party' }
	];
</script>

<Gallery {isOpen} {toggle} bind:index images={bakingImages.map((i) => i.src)} />

<Row class="ms-5 gy-3 gx-3">
	{#each bakingImages as img, i}
		<Col md="6">
			<button
				class="btn p-0 m-0 position-relative"
				style:border="none"
				on:click={() => {
					openGallery(i);
				}}
			>
				<img src={img.src} class="square w-100 h-100" alt="Baking Gallery" />
				<div class="w-100 h-100 position-absolute text-center hover d-flex align-items-center">
					<div style:font-size="20px" class="text-white m-auto">
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
		background: rgba(128, 128, 128, 0.4);
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
