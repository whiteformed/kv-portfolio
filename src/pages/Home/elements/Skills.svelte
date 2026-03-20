<script lang="ts">
	const SKILLSET = [
		{
			type: 'Hard Skills',
			set: [
				'Глубинные интервью, UX-тестирование, применение фреймворков: JTBD, сегментация аудитории',
				'Анализ конкурентов',
				'Проектирование логики интерфейса (информационная архитектура, user flow)',
				'Работа в Figma (вайрфреймы, auto-layouts, variables, components, интерактивные прототипы)',
				'Передача макетов в разработку (UI-kit/дизайн-система, аккуратная организация рабочего файла)',
			],
		},
		{
			type: 'Soft Skills',
			set: [
				'Глубоко погружаюсь в проект, задавая правильные вопросы',
				'Прорабатываю задачу, исходя из потребности бизнеса и понимания ценности для пользователя',
				'Проектирую с учетом технических ограничений',
				'Понимаю важность здоровой коммуникации внутри команды',
				'Ориентирована на расширение своих компетенций',
			],
		},
	];
</script>

<div class="grid grid-cols-2 gap-6 not-lg:grid-cols-1">
	{#each SKILLSET as { type, set } (type)}
		<div class="flex-1">
			<span class="text-2xl font-bold">
				<span class="text-4xl font-bold">{type}</span>
			</span>
			<div class="mt-4 flex-1">
				<span class="text-xl">
					{#each set as skill, index (index)}
						<li class="mt-1 ml-4">{skill}</li>
					{/each}
				</span>
			</div>
		</div>
	{/each}
</div>
