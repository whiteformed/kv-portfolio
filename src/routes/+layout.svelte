<script lang="ts">
	import './layout.css';
	import { page } from '$app/state';
	import KVV from '$lib/assets/KVV.svg';
	import type { Snippet } from 'svelte';

	type Props = {
		children: Snippet;
	};
	const { children }: Props = $props();

	function getTitleByPathName(path: typeof page.url.pathname) {
		switch (path) {
			case '/cases/sber-university/':
				return 'Кейс | ☁️ СберУниверситет / Медиатека';
			case '/cases/market-twits/':
				return 'Кейс | 🌐 MarketTwits / Новостной агрегатор';
			case '/cases/texol/':
				return 'Кейс | 🛠️ Цифровой инспектор';

			default:
				return 'Портфолио | Валерия Карлова – продуктовый дизайнер';
		}
	}
</script>

<svelte:head>
	<link rel="icon" href={KVV} />
	<title>{getTitleByPathName(page.url.pathname)}</title>
	<meta name="description" content="Валерия Карлова | Портфолио" />

	<meta property="og:site_name" content="Валерия Карлова | Портфолио" />
	<meta property="og:title" content="Валерия Карлова | Портфолио" />
	<meta property="og:type" content="portfolio" />

	<meta property="og:image" content={KVV} />
	<meta property="og:image:width" content="1200" />
	<meta property="og:image:height" content="630" />
	<meta property="og:image:alt" content="Валерия Карлова | Портфолио" />
	<meta property="og:image:type" content="image/webp" />
</svelte:head>

<main class="py-7">
	{@render children()}
</main>
