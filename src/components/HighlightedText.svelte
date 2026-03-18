<script lang="ts">
	import type { Snippet } from 'svelte';
	import type { HTMLAttributes } from 'svelte/elements';
	import { twMerge } from 'tailwind-merge';
	import type { ClassNameValue } from 'tailwind-merge';

	type Props = HTMLAttributes<HTMLSpanElement> & {
		class?: ClassNameValue;
		children: Snippet;
	};

	const { children, class: classNameValue, ...props }: Props = $props();
</script>

<span
	class={twMerge('inline-block rounded bg-cyan-900 p-1 text-cyan-300 opacity-70', classNameValue)}
	{...props}
>
	{@render children()}
</span>
