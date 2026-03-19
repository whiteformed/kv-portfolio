<script lang="ts">
	import './layout.css';
	import { page } from '$app/state';
	import favicon from '$lib/assets/favicon.svg';
	import type { Snippet } from 'svelte';

	type Props = {
		children: Snippet;
	};
	const { children }: Props = $props();

	function getTitleByPathName(path: typeof page.url.pathname) {
		switch (path) {
			case '/cases/sber-university':
				return 'Кейс | ☁️ СберУниверситет / Медиатека';
			case '/cases/market-twits':
				return 'Кейс | 🌐 MarketTwits / Новостной агрегатор';
			case '/cases/texol':
				return 'Кейс | 🛠️ Цифровой инспектор';

			default:
				return 'Резюме | Валерия Карлова – продуктовый дизайнер';
		}
	}
</script>

<svelte:head>
	<title>{getTitleByPathName(page.url.pathname)}</title>
	<link rel="icon" href={favicon} />
</svelte:head>

<div class="py-7">
	{@render children()}
</div>
