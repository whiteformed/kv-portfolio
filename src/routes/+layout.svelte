<script lang="ts">
	import './layout.css';
	import { page } from '$app/state';
	import favicon from '$images/favicon.png';
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
				return 'Карлова Валерия – продуктовый дизайнер | Портфолио';
		}
	}
</script>

<svelte:head>
	<link rel="icon" href={favicon} type="image/png" />
	<title>{getTitleByPathName(page.url.pathname)}</title>
	<meta name="description" content="Карлова Валерия | Личный сайт | Портфолио" />

	<meta property="og:site_name" content="Карлова Валерия – продуктовый дизайнер" />
	<meta property="og:title" content="Карлова Валерия" />
	<meta property="og:description" content="Личный сайт | Портфолио" />
	<meta property="og:url" content="https://karlova-valeria.ru/" />
	<meta property="og:image" content={favicon} />

	<meta property="og:image:width" content="1200" />
	<meta property="og:image:height" content="630" />
	<meta
		property="og:image:alt"
		content="Карлова Валерия | Продуктовый дизайнер | Личный сайт | Портфолио"
	/>
	<meta property="og:type" content="website" />
</svelte:head>

<main class="py-7">
	{@render children()}
</main>
