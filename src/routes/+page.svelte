<script lang="ts">
	import PostWithGallery from '$lib/PostWithGallery.svelte';
	import PostWithVideo from '$lib/PostWithVideo.svelte';
	import TikTokThumbnail from '$lib/TikTokThumbnail.svelte';
	import { IconPlayerPlayFilled } from '@tabler/icons-svelte';
	import { base } from '$app/paths';
	import CreativeHighlights from '$lib/CreativeHighlights.svelte';

	let v1PreviousViewable = false;
	let v2PreviousViewable = false;
	let v3PreviousViewable = false;
	let v1Viewable: boolean;
	let v2Viewable: boolean;
	let v3Viewable: boolean;
	let v1Paused = true;
	let v2Paused = true;
	let v3Paused = true;

	$: {
		// TODO less hacky
		if (v1Viewable != v1PreviousViewable) {
			if (v1Viewable) {
				v1Paused = false;
				v2Paused = true;
				v3Paused = true;
			} else {
				v1Paused = true;
			}
			v1PreviousViewable = v1Viewable;
		} else if (v2Viewable != v2PreviousViewable) {
			if (v2Viewable) {
				v1Paused = true;
				v2Paused = false;
				v3Paused = true;
			} else {
				v2Paused = true;
				v3Paused = !v3Viewable;
			}
			v2PreviousViewable = v2Viewable;
		} else if (v3Viewable != v3PreviousViewable) {
			if (v3Viewable) {
				v1Paused = true;
				v2Paused = true;
				v3Paused = false;
			} else {
				v2Paused = !v2Viewable;
				v3Paused = true;
			}
			v3PreviousViewable = v3Viewable;
		}
	}

	let bakingImages = [
		`${base}/cookies/xmas1.jpg`,
		`${base}/cookies/easter.jpg`,
		`${base}/cookies/xmas3.jpg`,
		`${base}/cookies/cvs1.jpg`,
		`${base}/cookies/duke.jpg`,
		`${base}/cookies/xmas2.jpg`,
		`${base}/cookies/dog.jpg`,
		`${base}/cookies/cvs2.jpg`,
		`${base}/cookies/alabama.jpg`,
		`${base}/cookies/newyork.jpg`,
		`${base}/cookies/disco.jpg`,
		`${base}/cookies/wedding.jpg`
	];
	let carolinaImages = [`${base}/carolina/carolina_ad.jpg`, `${base}/carolina/carolina_tees.jpg`];
	let cakeImages = [
		`${base}/cakes/guitar.jpg`,
		`${base}/cakes/meg.jpg`,
		`${base}/cakes/wedding.jpg`,
		`${base}/cakes/unc.jpg`,
		`${base}/cakes/mom.jpg`,
		`${base}/cakes/sophie.jpg`,
		`${base}/cakes/spiderman.jpg`,
		`${base}/cakes/chocolate.jpg`,
		`${base}/cakes/rose.jpg`,
		`${base}/cakes/baby_princess.jpg`,
		`${base}/cakes/kim.jpg`,
		`${base}/cakes/m.jpg`,
		`${base}/cakes/table.jpg`
	];
</script>

<div class="m-auto px-sm-2" style:max-width="600px">
	<div class="d-flex mb-4 mb-md-5">
		<div class="story-head d-flex flex-column align-items-center">
			<TikTokThumbnail story url="https://www.tiktok.com/t/ZT84duJXY/" img="tiktok/hairspray.jpg" />
			<div class="d-flex align-items-center">
				<IconPlayerPlayFilled class="d-inline me-1" size={16} /> 4.8M
			</div>
		</div>
		<div class="story-head d-flex flex-column align-items-center">
			<TikTokThumbnail story url="https://www.tiktok.com/t/ZT84d59wr/" img="tiktok/vitamix.jpg" />
			<div class="d-flex align-items-center">
				<IconPlayerPlayFilled class="d-inline me-1" size={16} /> 166K
			</div>
		</div>
		<div class="story-head d-flex flex-column align-items-center">
			<TikTokThumbnail story url="https://www.tiktok.com/t/ZT84dsYtm/" img="tiktok/apple.jpg" />
			<div class="d-flex align-items-center">
				<IconPlayerPlayFilled class="d-inline me-1" size={16} /> 5.3M
			</div>
		</div>
		<div class="story-head d-none d-md-flex flex-column align-items-center">
			<TikTokThumbnail story url="https://www.tiktok.com/t/ZT84d4fsU/" img="tiktok/cake.jpg" />
			<div class="d-flex align-items-center">
				<IconPlayerPlayFilled class="d-inline me-1" size={16} /> 51K
			</div>
		</div>
		<div class="story-head d-flex flex-column align-items-center">
			<TikTokThumbnail story url="https://www.tiktok.com/t/ZT84dp7tq/" img="tiktok/kdrama.jpg" />
			<div class="d-flex align-items-center">
				<IconPlayerPlayFilled class="d-inline me-1" size={16} /> 263K
			</div>
		</div>
		<div class="story-head d-flex flex-column align-items-center">
			<TikTokThumbnail story url="https://www.tiktok.com/t/ZT84dx22E/" img="tiktok/graduate.jpg" />
			<div class="d-flex align-items-center">
				<IconPlayerPlayFilled class="d-inline me-1" size={16} /> 1.7M
			</div>
		</div>
	</div>

	<PostWithGallery
		images={bakingImages}
		caption="I design and produce custom cookie orders for corporate events, weddings, birthdays, and more."
	/>

	<PostWithVideo
		bind:viewable={v1Viewable}
		bind:paused={v1Paused}
		src="custom_print.mp4"
		caption="Animation created using Jitter, CapCut, and iMovie to promote custom prints I drew of different universities
	across the US (note: website is no longer active)."
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
		bind:viewable={v2Viewable}
		bind:paused={v2Paused}
		src="la.mp4"
		caption="To advertise my print business, I animated quick, cheeky videos like this one to bring in more customers."
	/>

	<PostWithVideo
		bind:viewable={v3Viewable}
		bind:paused={v3Paused}
		src="berkeley.mp4"
		caption="Each print is drawn with an Apple Pencil on iPad Pro using Procreate"
	/>

	<div class="d-block d-lg-none">
		<CreativeHighlights />
	</div>
</div>

<style>
	.story-head {
		font-size: 0.9rem;
		color: #222;
		gap: 2px;
		width: 0;
		flex: 1 1 0;
	}
	.story-head:not(:last-child) {
		margin-right: 8px;
	}
</style>
