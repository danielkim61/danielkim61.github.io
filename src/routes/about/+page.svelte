<script lang="ts">
	import Avatar from '$lib/Avatar.svelte';
	import { Container } from '@sveltestrap/sveltestrap';
</script>

<Container class="ps-sm-5 pe-lg-5">
	<div class="position-relative" style:max-width="840px">
		<div class="ps-2 pe-4 pb-2">
			<Avatar size={144} />
			<div class="ps-3 position-relative" style:max-width="700px">
				<p class="pt-4">Hello! I’m Daniel.</p>
				<p>
					I work in 
					<a
						href="https://www.lyft.com/transit/partnerships"
					>
						Transit and EDU partnerships</a
					> at Lyft. Prior to that, I was in the
					<a
						href="https://jobs.cvshealth.com/general-management-talent-programs/general-management-development-program/"
					>
						General Management Development Program</a
					>, sponsored by CVS President and CEO, Karen Lynch. 
				</p>
				<p>Outside of tech, I enjoy a host of creative endeavors:</p>

				<ul>
					<li>
						I run a professional baking business which has catered cakes and cookies for weddings,
						corporate events, and birthday parties. I have done graphic design work which I sold to
						various top-tier universities, and I used to run a gift-wrapping nonprofit.
					</li>
					<li>
						I'm well-versed in the current social media landscape – I have a lifestyle TikTok with
						22k followers, more than 20 million total views, and have done brand deals with Adobe,
						Hims & Hers, Match Group, Truff and others. I understand how to cultivate an audience
						and what makes content relatable and interesting.
					</li>
					<li>
						I have some experience writing code in Python and RStudio from research I co-published
						in "Circulation" which modeled cardiovascular health at a county level in North
						Carolina.
					</li>
				</ul>
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
	p,
	li {
		line-height: 2rem;
	}
</style>
