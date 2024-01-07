<script lang="ts">
	import DanielAvatar from '$lib/DanielAvatar.svelte';
	import Post from '$lib/Post.svelte';
	import IntersectionObserver from 'svelte-intersection-observer';

	var videoElement: HTMLVideoElement;

	export let src: string;
	export let caption: string;
</script>

<Post>
	<IntersectionObserver
		element={videoElement}
		threshold={0.5}
		on:observe={(e) => {
			if (e.detail.isIntersecting) {
				videoElement.play();
			} else {
				videoElement.pause();
			}
		}}
	>
		<!-- svelte-ignore a11y-media-has-caption -->
		<video class="w-100" bind:this={videoElement} muted loop controls>
			<source {src} />
			Your browser does not support the video tag.
		</video>
	</IntersectionObserver>
	<div class="graybox p-2">
		<DanielAvatar class="d-inline-block align-top" />
		<strong>Daniel</strong>
		{caption}
	</div>
</Post>
