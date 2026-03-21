<script lang="ts">
	import Carousel from './Carousel/Carousel.svelte';
	import CarouselSlide from './Carousel/CarouselSlide.svelte';
	import Modal from './Modal.svelte';
	import type { HTMLImgAttributes } from 'svelte/elements';
	import { twMerge, type ClassNameValue } from 'tailwind-merge';
	import { v4 as uuidv4 } from 'uuid';

	type Props = HTMLImgAttributes & {
		src: string;
		groupId?: string;
		useViewer?: boolean;
		class?: ClassNameValue;
	};

	const {
		src,
		fetchpriority = 'high',
		alt,
		groupId = uuidv4(),
		class: classNameValue,
		useViewer = false,
		draggable = false,
		...props
	}: Props = $props();

	const DATA_GROUP_ATTR = 'data-image-group';

	let ref = $state<HTMLElement>();

	const dataAttributes = $derived({
		...(groupId && { [DATA_GROUP_ATTR]: groupId }),
	});
	const imageGroup = $derived(
		[...document.querySelectorAll(`[${DATA_GROUP_ATTR}="${groupId}"]`)].map((node) =>
			node.cloneNode(true),
		),
	);

	let visible = $state(false);

	function handleToggle() {
		visible = !visible;
	}

	function renderNode(nodeToRender: Node) {
		return (node: HTMLElement) => {
			node.appendChild(nodeToRender);
		};
	}
</script>

{#snippet image()}
	<enhanced:img
		bind:this={ref}
		{src}
		{fetchpriority}
		{alt}
		class={twMerge(classNameValue, useViewer && 'cursor-pointer')}
		{draggable}
		onclick={handleToggle}
		{...dataAttributes}
		{...props}
	/>
{/snippet}

{#if useViewer}
	<Modal bind:visible>
		<div class="h-full w-full max-w-8/10 max-h-8/10 not-md:max-w-full">
			<Carousel>
				{#each imageGroup as image, index (index)}
					<CarouselSlide>
						<div {@attach renderNode(image)}></div>
					</CarouselSlide>
				{/each}
			</Carousel>
		</div>
	</Modal>
{/if}
{@render image()}
