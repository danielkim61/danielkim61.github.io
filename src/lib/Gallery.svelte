<script lang="ts">
	import { Container, Modal, Row, Col } from '@sveltestrap/sveltestrap';

	export let isOpen: boolean;
	export let toggle: () => void;

	export let images: string[];
	export let index = 0;
</script>

<Modal
	body
	size="lg"
	{isOpen}
	{toggle}
	on:close={() => {
		index = 0;
	}}
>
	<Container class="h-100 d-flex align-items-center">
		<div class="align-items-center d-flex flex-grow-1">
			<div>
				<button
					class="btn btn-plain"
					on:click={() => {
						index = (index - 1) % images.length;
						if (index < 0) {
							index = images.length - 1;
						}
					}}
				>
					&lt;
				</button>
			</div>
			<div class="text-center flex-grow-1">
				<img class="img-fluid" style:max-height="500px" src={images[index]} alt="Gallery" />
			</div>
			<div>
				<button class="btn btn-plain" on:click={() => (index = (index + 1) % images.length)}>
					&gt;
				</button>
			</div>
		</div>
	</Container>
</Modal>

<style>
	button {
		font-size: 20px;
		font-weight: bold;
	}
	:global(.modal-content) {
		background-color: rgba(255, 255, 255, 0.9);
		height: 100%;
	}
	:global(.modal-dialog) {
		height: 80% !important;
	}
</style>
