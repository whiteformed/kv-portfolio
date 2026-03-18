<script lang="ts">
	import type { Snippet } from 'svelte';
	import type { HTMLAttributes } from 'svelte/elements';
	import { twMerge } from 'tailwind-merge';
	import type { ClassNameValue } from 'tailwind-merge';

	type Props = HTMLAttributes<HTMLDivElement> & {
		class?: ClassNameValue;
		children: Snippet;
	};

	const { children, class: classNameValue, ...props }: Props = $props();
</script>

<div
	class={twMerge(
		'flex w-fit items-center justify-center rounded bg-gray-800 px-2 py-1 text-center text-gray-400',
		classNameValue,
	)}
	{...props}
>
	{@render children()}
</div>
