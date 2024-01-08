<script lang="ts">
	import Gallery from '$lib/Gallery.svelte';
	import { Col, Row } from '@sveltestrap/sveltestrap';

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
		{ src: '/cookies/xmas3.jpg', caption: 'Classic Christmas Cookie Order' },
		{ src: '/cakes/rose.jpg', caption: 'Garden Party Cake' },
		{ src: '/cakes/unc.jpg', caption: 'UNC Chapel Hill Graduation Cake' },
		{ src: '/cookies/xmas1.jpg', caption: 'Modern Christmas Cookie Order' },
		{ src: '/cookies/dog.jpg', caption: 'BarkBox™ Cookie Order' },
		{ src: '/cakes/guitar.jpg', caption: 'Rock & Roll Cake Order' },
		{ src: '/cookies/duke.jpg', caption: 'Duke University Winter Event' },
		{ src: '/cookies/newyork.jpg', caption: "New Year's Eve Wedding Cookie Order" },
		{ src: '/cakes/wedding.jpg', caption: 'Three-Tier Fondant Wedding Cake' },
		{ src: '/cookies/cvs1.jpg', caption: 'CVS Health Philadelphia Corporate Event' },
		{ src: '/cookies/xmas2.jpg', caption: 'Holiday Cookie Order' },
		{ src: '/cookies/easter.jpg', caption: 'Easter Tea Party Cookie Order' },
		{ src: '/cookies/cvs2.jpg', caption: 'CVS Health NYC Corporate Event' },
		{ src: '/cakes/spiderman.jpg', caption: 'Spiderman-Themed Birthday Cake' },
		{ src: '/cookies/alabama.jpg', caption: 'University of Alabama Cookie Order' },
		{ src: '/cookies/disco.jpg', caption: 'Disco Bridal Shower Cookie Order' },
		{ src: '/cakes/meg.jpg', caption: 'Birthday Cake Order' },
		{ src: '/cakes/mom.jpg', caption: 'Floral Birthday Cake' },
		{ src: '/cakes/sophie.jpg', caption: 'Princess-Themed Birthday Cake' },
		{ src: '/cakes/chocolate.jpg', caption: 'Chocolate Birthday Cake' },
		{ src: '/cakes/baby_princess.jpg', caption: 'Baby Princess Cake' },
		{ src: '/cakes/kim.jpg', caption: 'Spring Birthday Cake' },
		{ src: '/cakes/m.jpg', caption: 'Gatsby-Themed Three-Tier Birthday Cake' },
		{ src: '/cakes/table.jpg', caption: 'UNC Chapel Hill Graduation Party' }
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
