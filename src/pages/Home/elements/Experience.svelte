<script lang="ts">
	import Link from '$components/Link.svelte';

	const EXPS = [
		{
			companyName: 'Datagile',
			companyLink: 'https://datagile.ru/',
			employedTime: 'апрель 2025 – настоящее время',
			jobDone: {
				'': [
					'Проектирование пользовательских сценариев и интерфейсов для web',
					'Создание и развитие дизайн-системы на несколько продуктов',
					'User flow, JTBD, проведение интервью, анализ конкурентов',
					'Создание интерактивных прототипов и микро-анимаций ',
					'Проведение UX-аудита и оптимизация существующих решений',
					'Взаимодействие с командой по Agile:Scrum',
					'Дизайн-ревью',
					'Презентация решений команде и стейкхолдерам',
				],
			},
		},
		{
			companyName: 'Delonix.io',
			companyLink: '',
			employedTime: 'декабрь 2023 – март 2025',
			jobDone: {
				'Поддержка сайта и личного кабинета криптобота для автоматизированного трейдинга:': [
					'Проектирование пользовательского интерфейса для web и mobile',
					'Доработка существующих сценариев взаимодействия и создание новых',
					'Редизайн',
					'Рефакторинг компонентов, доработка дизайн-системы',
					"Генерация идей с product owner'ом",
					'Подготовка макетов к разработке',
					'Дизайн-ревью',
				],
			},
		},
		{
			companyName: 'IBS Dunice',
			companyLink: 'https://dunice.net/ru',
			employedTime: 'май 2020 – декабрь 2023',
			jobDone: {
				'': [
					'Проектирование пользовательских сценариев и интерфейсов для web и mobile',
					'Создание дизайн-концепций',
					'Создание и развитие UI-китов и дизайн-систем',
					'User flow, JTBD, проведение интервью, UX-тестирование, создание персон, анализ конкурентов',
					'Создание интерактивных прототипов и микро-анимаций',
					'Проведение UX-аудита и оптимизация существующих решений',
					'Взаимодействие с командой по Agile:Scrum',
					'Дизайн-ревью',
					'Презентация решений команде и проделанной работы клиенту',
					'Участие в тендерах',
					'Написание и редактура текстов',
					'Создание иконок, баннеров и других графических элементов',
				],
			},
		},
	] as const;
</script>

<div class="flex flex-col items-start gap-6 not-lg:gap-4">
	<span class="text-4xl font-bold">Опыт</span>

	<div class="grid grid-cols-2 gap-10 not-lg:grid-cols-1 not-lg:gap-6">
		{#each EXPS as { companyName, companyLink, employedTime, jobDone } (companyName)}
			<div class="flex-1">
				<span class="text-2xl font-bold">
					{#if companyLink}
						<Link href={companyLink} rel="external" target="_blank">
							{companyName}
						</Link>
					{:else}
						{companyName}
					{/if}
					{employedTime}
				</span>
				<div class="mt-4 flex-1">
					<span class="text-xl">
						{#each Object.entries(jobDone) as [groupName, values], index (index)}
							{#if groupName}
								{groupName}
							{/if}
							{@const points = values as string[]}

							<ul>
								{#each points as point, index (index)}
									<li class="mt-1 ml-4">{point}</li>
								{/each}
							</ul>
						{/each}
					</span>
				</div>
			</div>
		{/each}
	</div>
</div>
