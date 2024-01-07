<script lang="ts">
	var classes = '';
	export { classes as class };

	export let size = 24;
</script>

<div class="position-relative {classes}" style:width="{size}px" style:height="{size}px">
	<img
		style:width="{size}px"
		style:height="{size}px"
		class="avatar-size avatar-position"
		src="daniel_headshot.jpg"
		style:border-radius="50%"
		alt="Daniel headshot"
	/>
	<div class="avatar-border avatar-position w-100 h-100" />
</div>

<style>
	.avatar-position {
		position: absolute;
		top: 0;
		left: 0;
	}
	.avatar-border {
		border: 1px solid rgba(0, 0, 0, 0.2);
		border-radius: 50%;
	}
</style>
