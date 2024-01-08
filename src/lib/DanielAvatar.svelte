<script lang="ts">
	var classes = '';
	export { classes as class };

	export let size = 24;
	export let src = '/memoji.jpg';
</script>

<img
	style:width="{size}px"
	style:height="{size}px"
	class="avatar-size avatar-position {classes}"
	{src}
	style:border-radius="50%"
	alt="Daniel avatar"
/>
