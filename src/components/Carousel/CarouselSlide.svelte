<script lang="ts">
	import type { Snippet } from 'svelte';
	import type { HTMLAttributes } from 'svelte/elements';
	import type { ClassNameValue } from 'tailwind-merge';

	type Props = HTMLAttributes<HTMLDivElement> & {
		class?: ClassNameValue;
		children: Snippet;
	};

	const { class: classNameValue, children }: Props = $props();
</script>

<div class={['carousel-slide', classNameValue]}>
	{@render children()}
</div>

<style>
	.carousel-slide {
		flex: 0 0 100%;
		min-width: 0;
	}
</style>
