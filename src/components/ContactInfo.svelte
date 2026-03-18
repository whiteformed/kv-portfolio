<script>
	import Link from '$components/Link.svelte';

	const LINKS_LIST = [
		{ href: 'https://t.me/karl0va', text: 'telegram' },
		{ href: 'mailto:karlowa.valeria@yandex.ru', text: 'karlowa.valeria@yandex.ru' },
		{ href: 'https://disk.yandex.ru/i/QsyJ7kCFJROLSA', text: '🔗 CV' },
	];
</script>

<div class="flex w-full flex-row flex-wrap gap-2 not-md:flex-col not-md:gap-0">
	{#each LINKS_LIST as { href, text }, index (text)}
		<Link {href} target="_blank">{text}</Link>
		{#if index !== LINKS_LIST.length - 1}
			<span class="text-white">·</span>
		{/if}
	{/each}
</div>
