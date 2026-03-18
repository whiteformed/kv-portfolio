<script lang="ts">
	import { ImageViewer } from 'svelte-image-viewer';
	import type { HTMLImgAttributes } from 'svelte/elements';
	import { twMerge, type ClassNameValue } from 'tailwind-merge';

	type Props = HTMLImgAttributes & {
		useViewer?: boolean;
		class?: ClassNameValue;
	};

	const {
		src,
		alt,
		class: classNameValue,
		useViewer = false,
		draggable = false,
		...props
	}: Props = $props();

	let isOpen = $state();

	function handleToggle() {
		isOpen = !isOpen;
	}
	function handleClose() {
		isOpen = false;
	}

	function handleKeyDown(event: KeyboardEvent) {
		if (event.code === 'Escape') {
			handleClose();
		}
	}
</script>

<!--  TODO: change to element press handler / outside click -->
<svelte:window onkeydown={handleKeyDown} />

{#snippet image()}
	<img
		{src}
		{alt}
		class={twMerge(classNameValue, useViewer && 'cursor-pointer')}
		{draggable}
		onclick={handleToggle}
		{...props}
	/>
{/snippet}

{#if useViewer && src && isOpen}
	<div class={['fixed left-0 top-0 h-full w-full z-10 isolate', 'viewer']} role="dialog">
		<button
			class="absolute top-6 right-6 z-10 cursor-pointer hover:shadow text-2xl text-white hover:text-gray-300"
			onclick={handleClose}
		>
			X
		</button>
		<ImageViewer {src} alt={alt || ''} targetScale={0.8} />
	</div>
{:else}
	{@render image()}
{/if}

<style>
	.viewer {
		backdrop-filter: blur(0.5rem);
	}
</style>
