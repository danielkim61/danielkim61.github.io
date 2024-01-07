<script lang="ts">
	import DanielAvatar from '$lib/DanielAvatar.svelte';
	import Post from '$lib/Post.svelte';
	import IntersectionObserver from 'svelte-intersection-observer';

	export let src: string;
	export let caption: string;
	export let viewable = false;
	export let paused: boolean;

	let videoElement: HTMLVideoElement;
</script>

<Post>
	<IntersectionObserver
		element={videoElement}
		threshold={0.5}
		on:observe={(e) => (viewable = e.detail.isIntersecting)}
	>
		<!-- svelte-ignore a11y-media-has-caption -->
		<video class="w-100" bind:paused bind:this={videoElement} muted loop controls>
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
