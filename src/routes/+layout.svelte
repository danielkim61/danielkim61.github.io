<script lang="ts">
	import Menu from '$lib/Menu.svelte';
	import { page } from '$app/stores';
	import CreativeHighlights from '$lib/CreativeHighlights.svelte';
	import { base } from '$app/paths';
	import {
		Collapse,
		Dropdown,
		Nav,
		NavItem,
		NavLink,
		Navbar,
		NavbarBrand,
		NavbarToggler
	} from '@sveltestrap/sveltestrap';

	let isOpen = false;
	function handleUpdate(event: CustomEvent<boolean>) {
		isOpen = event.detail;
	}
</script>

<div class="container">
	<!-- TODO Refactor with Menu component -->
	<Navbar class="d-sm-none" sticky="top" light={true} color="white">
		<NavbarToggler on:click={() => (isOpen = !isOpen)} />
		<NavbarBrand href="{base}/" class="title">Daniel Kim</NavbarBrand>
		<Collapse {isOpen} navbar expand="md" on:update={handleUpdate}>
			<Nav class="ms-auto" navbar>
				<a class="nav-link mt-1" href="{base}/">
					<span class="emoji">🏠</span>
					<span class="menu-title" class:current={$page.url.pathname == `${base}/`}>Home</span>
				</a>
				<a class="nav-link" href="{base}/about/">
					<span class="emoji">🙋🏻‍♂️</span>
					<span class="menu-title" class:current={$page.url.pathname.startsWith(`${base}/about`)}
						>About</span
					>
				</a>
				<a class="nav-link" href="{base}/baking/">
					<span class="emoji">🍰</span>
					<span class="menu-title" class:current={$page.url.pathname.startsWith(`${base}/baking`)}
						>Baking</span
					>
				</a>
				<a class="nav-link" href="{base}/design/">
					<span class="emoji">🎨</span>
					<span class="menu-title" class:current={$page.url.pathname.startsWith(`${base}/design`)}
						>Graphic Design</span
					>
				</a>
				<a class="nav-link" href="{base}/social_media/">
					<span class="emoji">📱</span>
					<span
						class="menu-title"
						class:current={$page.url.pathname.startsWith(`${base}/social_media`)}>Social Media</span
					>
				</a>
				<a class="nav-link" href="{base}/contact/">
					<span class="emoji">👨🏻‍💻</span>
					<span class="menu-title" class:current={$page.url.pathname.startsWith(`${base}/contact`)}
						>Contact</span
					>
				</a>
			</Nav>
		</Collapse>
	</Navbar>

	<div class="d-flex">
		<Menu />
		<div class="col pt-4">
			<slot />
		</div>
		{#if $page.url.pathname == `${base}/`}
			<div class="d-none d-lg-block vh-100 sticky-top py-4">
				<CreativeHighlights />
			</div>
		{/if}
	</div>
</div>

<style>
	:global(.title) {
		font-size: 24px;
		font-weight: 600;
	}

	.emoji {
		font-size: 24px;
	}
	.menu-title {
		font-size: 20px;
		font-weight: 500;
		padding-left: 0.5rem;
		text-decoration: underline;
		text-decoration-thickness: 1px;
		text-underline-offset: 3px;
		text-decoration-color: rgba(0, 0, 0, 0);
		transition: text-decoration-color 0.2s ease;
	}
	.menu-title.current,
	.menu-title:hover {
		text-decoration-color: rgba(0, 0, 0, 0.4);
	}
</style>
