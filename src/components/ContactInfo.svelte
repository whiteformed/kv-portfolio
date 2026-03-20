<script>
	import Link from '$components/Link.svelte';

	const LINKS_LIST = [
		{ href: 'https://t.me/karl0va', text: 'telegram' },
		{ href: 'mailto:karlowa.valeria@yandex.ru', text: 'karlowa.valeria@yandex.ru' },
		{ href: 'https://disk.yandex.ru/i/QsyJ7kCFJROLSA', text: '🔗 CV' },
	];
</script>

<div class="flex w-full flex-row flex-wrap not-sm:flex-col gap-2 not-sm:gap-0">
	{#each LINKS_LIST as { href, text }, index (text)}
		{@const last = LINKS_LIST.length - 1 === index}
		{console.log(last)}
		<div class="flex flex-row gap-2 not-sm:flex-row-reverse not-sm:justify-end">
			<Link {href} target="_blank">{text}</Link>
			<span class={['text-white', last && 'sm:hidden']}> · </span>
		</div>
	{/each}
</div>
