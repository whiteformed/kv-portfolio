<script lang="ts">
	import { resolve } from '$app/paths';
	import Image from '$components/Image.svelte';
	import Link from '$components/Link.svelte';
	import MarketTwitsPreview from '$lib/assets/MarketTwits/MarketTwitsPreview.webp';
	import SberUniversityPreview from '$lib/assets/SberUniversity/SberUniversityPreview.webp';
	import TexolPreview from '$lib/assets/Texol/TexolPreview.webp';

	const PATHS = [
		{
			title: '☁️ СберУниверситет / Медиатека',
			src: SberUniversityPreview,
			path: '/cases/sber-university',
		},
		{
			title: '🌐 MarketTwits / Новостной агрегатор',
			src: MarketTwitsPreview,
			path: '/cases/market-twits',
		},
		{
			title: '🛠️ Цифровой инспектор / Моб. приложение',
			src: TexolPreview,
			path: '/cases/texol',
		},
	] as const;
</script>

<div class="flex flex-col items-start gap-6">
	<span class="text-4xl font-bold">Кейсы</span>

	<div class="flex flex-col gap-6 lg:flex-row">
		{#each PATHS as { title, src, path } (path)}
			<Link
				href={resolve(path)}
				class="flex flex-1 cursor-pointer flex-col overflow-hidden rounded-2xl hover:-translate-y-2 active:-translate-y-2 transition-all shadow hover:shadow-blue-600 active:shadow-blue-600"
			>
				<Image {src} alt={title} class="h-fit" />
				<div
					class="text-l flex flex-1 flex-col justify-start rounded-b-2xl bg-blue-950 px-4 py-5 font-bold"
				>
					{title}
				</div>
			</Link>
		{/each}
	</div>
</div>
