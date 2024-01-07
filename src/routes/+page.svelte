<script lang="ts">
	import PostWithGallery from '$lib/PostWithGallery.svelte';
	import PostWithVideo from '$lib/PostWithVideo.svelte';
	import TikTokThumbnail from '$lib/TikTokThumbnail.svelte';
	import { onMount } from 'svelte';

	let bakingImages = [
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
		'cookies/wedding.jpg'
	];
	let carolinaImages = ['carolina/carolina_ad.jpg', 'carolina/carolina_tees.jpg'];
	let cakeImages = [
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
	];

	onMount(() => {
		// @ts-ignore
		if (typeof window.instgrm !== 'undefined') {
			// @ts-ignore
			window.instgrm.Embeds.process();
		}
	});
</script>

<div style:width="600px" class="m-auto">
	<div class="d-flex mb-5">
		<div class="story-head d-flex flex-column align-items-center">
			<TikTokThumbnail story url="https://www.tiktok.com/t/ZT84duJXY/" img="tiktok/hairspray.jpg" />
			▶️ 4.8M
		</div>
		<div class="story-head d-flex flex-column align-items-center">
			<TikTokThumbnail story url="https://www.tiktok.com/t/ZT84d59wr/" img="tiktok/vitamix.jpg" />
			▶️ 165K
		</div>
		<div class="story-head d-flex flex-column align-items-center">
			<TikTokThumbnail story url="https://www.tiktok.com/t/ZT84dsYtm/" img="tiktok/apple.jpg" />
			▶️ 5.3M
		</div>
		<div class="story-head d-flex flex-column align-items-center">
			<TikTokThumbnail story url="https://www.tiktok.com/t/ZT84d4fsU/" img="tiktok/cake.jpg" />
			▶️ 50.5K
		</div>
		<div class="story-head d-flex flex-column align-items-center">
			<TikTokThumbnail story url="https://www.tiktok.com/t/ZT84dp7tq/" img="tiktok/kdrama.jpg" />
			▶️ 262K
		</div>
		<div class="story-head d-flex flex-column align-items-center">
			<TikTokThumbnail story url="https://www.tiktok.com/t/ZT84dx22E/" img="tiktok/graduate.jpg" />
			▶️ 1.7M
		</div>
	</div>

	<PostWithGallery
		images={bakingImages}
		caption="I design and produce custom cookie orders for corporate events, weddings, birthdays, and more."
	/>

	<PostWithVideo
		src="custom_print.mp4"
		caption="Animation created using Jitter, CapCut, and iMovie to promote custom prints I drew of different universities
	across the US."
	/>

	<PostWithGallery
		images={carolinaImages}
		caption="In 2022, I worked directly with the head of UNC Chapel Hill student activities to create this design
which was printed on thousands of T-shirts given to UNC students on the first day of class."
	/>

	<PostWithGallery
		images={cakeImages}
		caption="I run a business which produces a few custom cakes every month. Each design is unique and based off the client's vision."
	/>

	<PostWithVideo
		src="la.mp4"
		caption="To advertise my print business, I animated quick, cheeky videos like this one to bring in more customers."
	/>
</div>

<style>
	:global(iframe.instagram-media) {
		position: static !important;
	}

	:global(.instagram-media),
	:global(.instagram-media-registered) {
		width: 600px !important;
	}

	.story-head {
		font-size: 0.9rem;
		color: #222;
		gap: 2px;
	}
	.story-head:not(:last-child) {
		margin-right: 8px;
	}
</style>
