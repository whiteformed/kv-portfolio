<script lang="ts">
	import type { EmblaPluginType } from 'embla-carousel';
	import type { EmblaCarouselType, EmblaOptionsType } from 'embla-carousel';
	import Autoplay from 'embla-carousel-autoplay';
	import useEmblaCarousel from 'embla-carousel-svelte';
	import type { Snippet } from 'svelte';

	type Props = {
		ref?: HTMLElement;
		emblaApi?: EmblaCarouselType;
		options?: EmblaOptionsType & {
			showDots?: boolean;
			autoPlay?: boolean;
		};
		children: Snippet;
	};

	let {
		ref = $bindable(),
		emblaApi = $bindable(),
		options: carouselOptions,
		children,
	}: Props = $props();

	const options = $derived({ loop: true, showDots: true, autoPlay: true, ...carouselOptions });

	let plugins: EmblaPluginType[] = $derived(options.autoPlay ? [Autoplay()] : []);

	let scrollSnaps: number[] = $state([]);
	let selectedSnap: number = $state(0);

	const scrollTo = (index: number) => {
		emblaApi?.scrollTo(index);
		selectedSnap = index;
	};
	const setupSnaps = (emblaApi: EmblaCarouselType) => {
		scrollSnaps = emblaApi.scrollSnapList();
	};
	const setActiveSnap = (emblaApi: EmblaCarouselType) => {
		selectedSnap = emblaApi.selectedScrollSnap();
	};

	const onInit = (event: CustomEvent<EmblaCarouselType>) => {
		emblaApi = event.detail;

		setupSnaps(emblaApi);
		setActiveSnap(emblaApi);

		emblaApi.on('reInit', setupSnaps);
		emblaApi.on('reInit', setActiveSnap);
		emblaApi.on('select', setActiveSnap);
	};

	function emblaCarousel(node: HTMLDivElement) {
		return useEmblaCarousel(node, { options, plugins });
	}
</script>

<div
	class="w-full h-full overflow-x-hidden overflow-y-scroll"
	use:emblaCarousel
	onemblaInit={onInit}
>
	<div class="flex touch-pan-y touch-pinch-zoom">
		{@render children()}
	</div>
	{#if options.showDots && scrollSnaps.length > 1}
		<div class="mt-4 flex justify-center">
			{#each scrollSnaps as snap, index (index)}
				{@const active = selectedSnap === index}
				<div
					data-snap={snap}
					role="button"
					tabindex="-1"
					onkeydown={null}
					class={`mx-2 inline-block size-2.5 cursor-pointer rounded-md bg-white ${active ? 'opacity-70' : 'opacity-40'} hover:opacity-100 active:opacity-100 transition-opacity`}
					onclick={() => scrollTo(index)}
					aria-label={`item #${index + 1}`}
				></div>
			{/each}
		</div>
	{/if}
</div>
