<script>
	import Badge from '$components/Badge.svelte';
	import ContactInfo from '$components/ContactInfo.svelte';
	import Image from '$components/Image.svelte';
	import Avatar from '$lib/assets/Avatar.webp';
</script>

<div class="flex flex-col items-start gap-6">
	<div>
		<Image src={Avatar} alt="Avatar" class="size-48 rounded-md" />
	</div>
	<div class="mt-4 flex flex-col items-start gap-2">
		<span class="text-4xl font-bold">Валерия Карлова – продуктовый дизайнер</span>
		<span class="text-l">Опыт работы: более 5 лет</span>
		<ContactInfo />

		<span class="my-4 text-xl font-extralight">
			Привет! Четыре года занимаюсь проектированием веб-интерфейсов, мобильных приложений и
			высоконагруженных систем. Ориентируюсь в гайдлайнах и понимаю, как строятся дизайн-системы.
			Понимаю и применяю принцип «делать≠сделать»
		</span>

		<div class="flex flex-row flex-wrap gap-2">
			{#each ['Figma', 'UX/UI', 'JTBD', 'User Flow', 'Анализ конкурентов', 'Дизайн-системы'] as text (text)}
				<Badge
					class="bg-green-950 text-lime-600 opacity-80 hover:opacity-100 hover:-translate-y-0.5 transition-all"
				>
					{text}
				</Badge>
			{/each}
		</div>
		<div class="flex flex-row flex-wrap gap-2">
			{#each ['Презентация', 'Организация работы', 'Коммуникация', 'Тайм-менеджмент'] as text (text)}
				<Badge
					class="bg-yellow-950 text-yellow-500 opacity-80 hover:opacity-100 hover:-translate-y-0.5 transition-all"
				>
					{text}
				</Badge>
			{/each}
		</div>
	</div>
</div>
