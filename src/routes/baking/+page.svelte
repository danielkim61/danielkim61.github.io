<script lang="ts">
	import Gallery from '$lib/Gallery.svelte';
	import Post from '$lib/Post.svelte';
	import { Col, Container, Row } from '@sveltestrap/sveltestrap';

	var isOpen = false;
	var index = 0;
	function toggle() {
		isOpen = !isOpen;
	}
	function openGallery(i: number) {
		isOpen = true;
		index = i;
	}

	function shuffle(array: any[]) {
		let currentIndex = array.length,
			randomIndex;

		// While there remain elements to shuffle.
		while (currentIndex > 0) {
			// Pick a remaining element.
			randomIndex = Math.floor(Math.random() * currentIndex);
			currentIndex--;

			// And swap it with the current element.
			[array[currentIndex], array[randomIndex]] = [array[randomIndex], array[currentIndex]];
		}

		return array;
	}

	let bakingImages = shuffle([
		'cookies/xmas1.jpg',
		'cookies/easter.jpg',
		'cookies/xmas3.jpg',
		'cookies/cvs1.jpg',
		'cookies/duke.jpg',
		'cookies/xmas2.jpg',
		'cookies/dog.jpg',
		'cookies/cvs2.jpg',
		'cookies/alabama.jpg',
		'cookies/newyork.jpg',
		'cookies/disco.jpg',
		'cookies/wedding.jpg',
		'cakes/guitar.jpg',
		'cakes/meg.jpg',
		'cakes/wedding.jpg',
		'cakes/unc.jpg',
		'cakes/mom.jpg',
		'cakes/sophie.jpg',
		'cakes/spiderman.jpg',
		'cakes/chocolate.jpg',
		'cakes/rose.jpg',
		'cakes/baby_princess.jpg',
		'cakes/kim.jpg',
		'cakes/m.jpg',
		'cakes/table.jpg'
	]);
</script>

<Gallery {isOpen} {toggle} bind:index images={bakingImages} />

<Row class="ms-5 gy-5 gx-5">
	{#each bakingImages as img, i}
		<Col md="6">
			<button
				class="btn p-0 m-0"
				style:border="0"
				on:click={() => {
					openGallery(i);
				}}
			>
				<Post roundCorners={false}>
					<img src={img} class="square w-100 h-100" alt="Baking Gallery" />
				</Post>
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
</style>
