<script lang="ts">
	import type { Snippet } from 'svelte';

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

	function transitionend(event: TransitionEvent) {
		const node = event.target as HTMLElement;
		node.focus();
	}

	function modalAction(node: HTMLElement) {
		const returnFn: (() => void)[] = [];

		if (document.body.style.overflow !== 'hidden') {
			const original = document.body.style.overflow;
			document.body.style.overflow = 'hidden';
			returnFn.push(() => {
				document.body.style.overflow = original;
			});
		}
		node.addEventListener('keypress', handleKeyDown);
		node.addEventListener('transitionend', transitionend);

		node.focus();

		returnFn.push(() => {
			node.removeEventListener('keypress', handleKeyDown);
			node.removeEventListener('transitionend', transitionend);
		});
		return {
			destroy: () => returnFn.forEach((fn) => fn()),
		};
	}
</script>

{#if visible}
	<div
		class="fixed top-0 left-0 w-full h-dvh flex items-center justify-center focus:outline-none"
		role="dialog"
		use:modalAction
		onkeydown={handleKeyDown}
		tabindex="-1"
	>
		<div
			class="backdrop bg-blend-overlay bg-black opacity-50 absolute w-full h-full"
			role="dialog"
			tabindex="-1"
			onclick={handleClose}
			onkeydown={handleKeyDown}
		></div>

		<div class="z-10 max-w-8/10 overflow-hidden not-md:max-w-full">
			<div class="content max-h-dvh overflow-auto">
				{@render children()}
			</div>
		</div>
	</div>
{/if}
