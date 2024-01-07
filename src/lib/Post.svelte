<script lang="ts">
	export let roundCorners = true;
</script>

<div class="post p-2 mb-4 {roundCorners ? 'post-rounded-corners' : ''}">
	<slot />
</div>

<style>
	.post {
		background: #fafafa;
		/* background: red; */
	}
	.post-rounded-corners {
		border-radius: 0 0 18px 18px;
	}
</style>
