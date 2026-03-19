<script lang="ts">
	import Modal from './Modal.svelte';
	import type { HTMLImgAttributes } from 'svelte/elements';
	import { twMerge, type ClassNameValue } from 'tailwind-merge';

	type Props = HTMLImgAttributes & {
		src: string;
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

	let visible = $state(false);

	function handleToggle() {
		visible = !visible;
	}
</script>

{#snippet image()}
	<enhanced:img
		{src}
		{alt}
		class={twMerge(classNameValue, useViewer && 'cursor-pointer')}
		{draggable}
		onclick={handleToggle}
		{...props}
	/>
{/snippet}

{#if useViewer}
	<Modal bind:visible>
		{@render image()}
	</Modal>
{/if}
{@render image()}
