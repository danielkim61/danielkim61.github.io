<script lang="ts">
	import Avatar from '$lib/Avatar.svelte';
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
		<video
			class="w-100"
			style:border-radius="12px"
			style:border=".5rem solid #f6f6f6"
			bind:paused
			bind:this={videoElement}
			muted
			loop
			controls
			playsinline
		>
			<source {src} />
			Your browser does not support the video tag.
		</video>
	</IntersectionObserver>
	<div class="graybox p-2">
		<Avatar class="d-inline-block align-top" />
		<strong>Daniel</strong>
		{caption}
	</div>
</Post>
