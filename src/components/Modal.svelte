<script lang="ts">
	import type { Snippet } from 'svelte';
	import { fly } from 'svelte/transition';

	type Props = {
		visible: boolean;
		children: Snippet;
	};
	let { visible = $bindable(), children }: Props = $props();

	function handleClose() {
		visible = false;
	}

	function handleKeyDown(event: KeyboardEvent) {
		event.stopPropagation();

		if (event.key === 'Escape') {
			handleClose();
		}
	}

	function portal(node: HTMLElement) {
		const body = document.body;
		body.appendChild(node);
		body.style.overflow = 'hidden';

		node.focus();

		return () => {
			body.style.overflow = 'initial';
		};
	}
</script>

{#if visible}
	<div
		{@attach portal}
		class="backdrop-blur fixed top-0 left-0 right-0 bottom-0 w-full flex items-center justify-center focus:outline-none"
		role="dialog"
		onclick={handleClose}
		onkeydown={handleKeyDown}
		tabindex="-1"
	>
		<div
			class="z-10 max-w-8/10 max-h-9/10 overflow-scroll not-md:max-w-full"
			in:fly={{ y: 300, duration: 300 }}
		>
			<div class="content h-full overflow-auto">
				{@render children()}
			</div>
		</div>
	</div>
{/if}
