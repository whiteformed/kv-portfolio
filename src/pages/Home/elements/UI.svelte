<script lang="ts">
	import Carousel from '$components/Carousel/Carousel.svelte';
	import CarouselSlide from '$components/Carousel/CarouselSlide.svelte';
	import Image from '$components/Image.svelte';
	import Carousel1 from '$lib/assets/Home/Carousel1.webp';
	import Carousel2 from '$lib/assets/Home/Carousel2.webp';
	import Carousel3 from '$lib/assets/Home/Carousel3.webp';

	const SLIDES = [Carousel1, Carousel2, Carousel3];
</script>

<div class="flex w-full flex-col items-start gap-6">
	<span class="text-4xl font-bold">UI</span>

	<Carousel>
		{#each SLIDES as src, index (src)}
			<CarouselSlide>
				<Image
					{src}
					alt={`Karlova Valeria, Shot ${index}`}
					referrerpolicy="no-referrer"
					class="rounded-4xl"
					useViewer
				/>
			</CarouselSlide>
		{/each}
	</Carousel>
</div>
