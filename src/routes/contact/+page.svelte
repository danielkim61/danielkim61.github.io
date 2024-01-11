<script lang="ts">
	import Avatar from '$lib/Avatar.svelte';
	import { Container } from '@sveltestrap/sveltestrap';
	import {
		IconBrandInstagram,
		IconBrandLinkedin,
		IconBrandTiktok,
		IconMail
	} from '@tabler/icons-svelte';
	import { base } from '$app/paths';
</script>

<Container class="ps-sm-5 pe-lg-5">
	<div class="position-relative" style:max-width="840px">
		<div class="ps-2 pe-4 pb-5">
			<Avatar src="{base}/contact_memoji.jpg" size={144} />
			<div class="ps-3" style:max-width="700px">
				<h2 class="pt-4 mb-3">Get in Touch</h2>
				<p>
					<a
						href="https://www.linkedin.com/in/daniel-kim-ddh/"
						target="_blank"
						class="d-flex align-items-center"
					>
						<IconBrandLinkedin />
						<span class="ps-2">Daniel Kim</span>
					</a>
				</p>
				<p>
					<a class="d-flex align-items-center" href="mailto:ddkim1441@gmail.com">
						<IconMail /> <span class="ps-2">ddkim1441@gmail.com</span>
					</a>
				</p>
				<p>
					<a
						class="d-flex align-items-center"
						target="_blank"
						href="https://www.instagram.com/ddkim61"
					>
						<IconBrandInstagram /> <span class="ps-2">@ddkim61</span>
					</a>
				</p>
				<p>
					<a
						class="d-flex align-items-center"
						target="_blank"
						href="https://www.tiktok.com/@ddkim61"
					>
						<IconBrandTiktok /> <span class="ps-2">@ddkim61</span>
					</a>
				</p>
			</div>
			<div
				class="graybox2 position-absolute"
				style:right="-20%"
				style:bottom="-40px"
				style:top="50%"
				style:left="50%"
				style:z-index="-20"
			/>
		</div>
		<div
			class="graybox position-absolute w-100"
			style:top="72px"
			style:bottom="0"
			style:z-index="-10"
		/>
	</div>
</Container>

<style>
	h2 {
		font-size: 24px;
		font-weight: 500;
	}
	p {
		line-height: 2rem;
		margin-bottom: 0.25rem;
	}
</style>
