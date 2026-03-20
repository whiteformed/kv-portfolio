<script lang="ts">
	import Badge from '$components/Badge.svelte';
	import ContactInfo from '$components/ContactInfo.svelte';
	import Image from '$components/Image.svelte';
	import Avatar from '$lib/assets/Avatar.webp';
	import { type ClassNameValue } from 'tailwind-merge';

	const BADGE_LIST_1 = [
		'Figma',
		'UX/UI',
		'JTBD',
		'User Flow',
		'Анализ конкурентов',
		'Дизайн-системы',
	];
	const BADGE_LIST_2 = ['Презентация', 'Организация работы', 'Коммуникация', 'Тайм-менеджмент'];
</script>

{#snippet badgeList(list: string[], mixin: ClassNameValue)}
	<div class="flex flex-row flex-wrap gap-2">
		{#each list as text (text)}
			<Badge
				class={[
					'opacity-80 hover:opacity-100 active:opacity-100 hover:-translate-y-0.5 active:-translate-y-0.5 transition-all',
					mixin,
				]}
			>
				{text}
			</Badge>
		{/each}
	</div>
{/snippet}

<div class="flex flex-col items-start gap-6 not-sm:gap-2">
	<div>
		<Image src={Avatar} alt="Avatar" class="size-48 rounded-md not-sm:size-40" />
	</div>
	<div class="mt-4 flex flex-col items-start gap-2 not-sm:mt-0">
		<span class="text-4xl font-bold">Валерия Карлова – продуктовый дизайнер</span>
		<span class="text-l">Опыт работы: более 5 лет</span>
		<ContactInfo />

		<span class="my-4 text-xl font-extralight whitespace-pre-line">
			{`Привет! Четыре года занимаюсь проектированием веб-интерфейсов, мобильных приложений и высоконагруженных систем. Ориентируюсь в гайдлайнах и понимаю, как строятся дизайн-системы.
			Понимаю и применяю принцип «делать≠сделать»`}
		</span>

		{@render badgeList(BADGE_LIST_1, 'bg-green-950 text-lime-600')}
		{@render badgeList(BADGE_LIST_2, 'bg-yellow-950 text-yellow-500')}
	</div>
</div>
