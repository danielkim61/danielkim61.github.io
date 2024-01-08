<script lang="ts">
	import { Container, Modal, Row, Col } from '@sveltestrap/sveltestrap';
	import { IconChevronLeft, IconChevronRight, IconX } from '@tabler/icons-svelte';

	export let isOpen: boolean;
	export let toggle: () => void;

	export let images: string[];
	export let index = 0;
</script>

<Modal
	body
	size="lg"
	modalClassName="gallery-modal"
	contentClassName="flex-column"
	{isOpen}
	{toggle}
	on:close={() => {
		index = 0;
	}}
>
	<div class="d-md-none position-absolute" style:top="0" style:left="0">
		<!-- svelte-ignore a11y-click-events-have-key-events -->
		<!-- svelte-ignore a11y-no-static-element-interactions -->
		<btn class="btn btn-link" style:color="inherit" style:border="none" on:click={toggle}
			><IconX /></btn
		>
	</div>
	<Container class="h-100 d-flex">
		<button
			class="btn btn-link ps-0 pe-1 px-sm-2"
			on:click={() => {
				index = (index - 1) % images.length;
				if (index < 0) {
					index = images.length - 1;
				}
			}}
		>
			<IconChevronLeft />
		</button>
		<div class="text-center d-flex align-items-center justify-content-center">
			<img src={images[index]} alt="Gallery" />
		</div>
		<button
			class="btn btn-link ps-1 pe-0 px-sm-2"
			on:click={() => (index = (index + 1) % images.length)}
		>
			<IconChevronRight />
		</button>
	</Container>
</Modal>

<style>
	button {
		font-size: 20px;
		font-weight: bold;
		border: none;
		color: inherit;
	}
	img {
		max-width: 100%;
		max-height: 100%;
	}
	:global(.gallery-modal .modal-body) {
		height: 100%;
		position: relative;
	}
	@media (max-width: 576px) {
		:global(.gallery-modal .modal-body) {
			padding: 0;
		}
	}

	:global(.gallery-modal .modal-content) {
		background-color: rgba(255, 255, 255, 0.9);
		height: 100%;
	}
	:global(.gallery-modal .modal-dialog) {
		height: 94%;
	}
</style>
