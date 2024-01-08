<script lang="ts">
	import { base } from '$app/paths';
	import { page } from '$app/stores';
</script>

<div class="py-4 vh-100 sticky-top">
	<div class="h-100 menu-border pe-5">
		<a class="mb-4 nav-link title" href="{base}/">Daniel Kim</a>
		<a class="mb-4 nav-link" href="{base}/">
			<span class="emoji">🏠</span>
			<span class="menu-title" class:current={$page.url.pathname == `${base}/`}>Home</span>
		</a>
		<a class="mb-4 nav-link" href="{base}/about/">
			<span class="emoji">🙋🏻‍♂️</span>
			<span class="menu-title" class:current={$page.url.pathname.startsWith(`${base}/about`)}
				>About</span
			>
		</a>
		<a class="mb-4 nav-link" href="{base}/baking/">
			<span class="emoji">🍰</span>
			<span class="menu-title" class:current={$page.url.pathname.startsWith(`${base}/baking`)}
				>Baking</span
			>
		</a>
		<a class="mb-4 nav-link" href="{base}/design/">
			<span class="emoji">🎨</span>
			<span class="menu-title" class:current={$page.url.pathname.startsWith(`${base}/design`)}
				>Graphic Design</span
			>
		</a>
		<a class="mb-4 nav-link" href="{base}/social_media/">
			<span class="emoji">📱</span>
			<span class="menu-title" class:current={$page.url.pathname.startsWith(`${base}/social_media`)}
				>Social Media</span
			>
		</a>
		<a class="mb-4 nav-link" href="{base}/contact/">
			<span class="emoji">👨🏻‍💻</span>
			<span class="menu-title" class:current={$page.url.pathname.startsWith(`${base}/contact`)}
				>Contact</span
			>
		</a>
	</div>
</div>

<style>
	.menu-border {
		border-right: 1px solid RGBA(0, 0, 0, 0.12);
	}
	.title {
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
	.nav-link {
		display: block;
	}
</style>
