<script lang="ts">
	import Carousel from '$components/Carousel/Carousel.svelte';
	import CarouselSlide from '$components/Carousel/CarouselSlide.svelte';
	import Image from '$components/Image.svelte';
	import Link from '$components/Link.svelte';
	import Carousel1 from '$images/Home/Carousel1.webp';
	import Carousel2 from '$images/Home/Carousel2.webp';
	import Carousel3 from '$images/Home/Carousel3.webp';
	import { v4 as uuidv4 } from 'uuid';

	const SLIDES = [Carousel1, Carousel2, Carousel3];
</script>

<div class="flex w-full flex-col items-start gap-6">
	<Link href="https://dribbble.com/Valeria6" rel="external" target="_blank">
		<span class="text-4xl font-bold">UI</span>
	</Link>

	<Carousel>
		{@const groupId = uuidv4()}
		{#each SLIDES as src, index (src)}
			<CarouselSlide>
				<Image
					{src}
					alt={`Dribbble Shot #${index}`}
					referrerpolicy="no-referrer"
					class="rounded-4xl"
					useViewer
					{groupId}
				/>
			</CarouselSlide>
		{/each}
	</Carousel>
</div>
