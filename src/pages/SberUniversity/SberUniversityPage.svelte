<script lang="ts">
	import Badge from '$components/Badge.svelte';
	import HighlightedText from '$components/HighlightedText.svelte';
	import Image from '$components/Image.svelte';
	import SberUniversityFlowExample1 from '$lib/assets/SberUniversity/SberUniversityFlowExample1.webp';
	import SberUniversityFlowExample2 from '$lib/assets/SberUniversity/SberUniversityFlowExample2.webp';
	import SberUniversityFlowExample3 from '$lib/assets/SberUniversity/SberUniversityFlowExample3.webp';
	import SberUniversityFlowExample4 from '$lib/assets/SberUniversity/SberUniversityFlowExample4.webp';
	import SberUniversityFlowExample5 from '$lib/assets/SberUniversity/SberUniversityFlowExample5.webp';
	import SberUniversityFlowExample6 from '$lib/assets/SberUniversity/SberUniversityFlowExample6.webp';
	import SberUniversityFlowExample7 from '$lib/assets/SberUniversity/SberUniversityFlowExample7.webp';
	import SberUniversityMain from '$lib/assets/SberUniversity/SberUniversityMain.webp';

	const ROLES_LIST = [
		{
			title: 'Админ',
			description:
				'Создание проектов, загрузка и редактирование файлов, добавление новых пользователей, управление учетными записями, просмотр истории действий, управление разделом спикеров',
		},
		{ title: 'Пользователь', description: 'Загрузка и редактирование файлов' },
	];

	const PROCESSES_LIST = [
		'После получения задачи, я принялась изучать существующий сервис',
		'Затем анализировала скринкасты пользователей по работе с сервисом, формулировала список вопросов для глубинных интервью, чтобы прояснить проблемы в основных сценариях',
		'Далее я проанализировала полученные ответы и приступила к генерации идей, параллельно изучая механики схожих сервисов',
		'После этого собрала первые итерации новых решений на прототипах и провела UX-тестирование',
		'Согласовала оптимальное решение со стейкхолдерами, подготовила макеты к разработке',
		'По готовности проводила ревью на тестовом стенде, описывала правки',
		'Затем обновления протестировали ранее опрошенные и новые пользователи – были отмечены интуитивность и простота взаимодействия с интерфейсом',
	];

	const JOBS_LIST = [
		'Спроектировала веб-интерфейс для внутренних сотрудников с ролевой моделью, систематизацией файлов и редактором видео-контента',
		'Выявляла и анализировала потребности пользователей с помощью глубинных интервью',
		'Взаимодействовала с разработчиками (фронт, бэк)',
		'Презентовала и защищала свои решения стейкхолдерам',
		'Работала с готовой дизайн-системой, при необходимости создавая на ее основе новые компоненты',
		"Взаимодействовала с product owner'ом, арт-директором и руководителем проекта",
	];
</script>

{#snippet imgWithSubtitle(src: string, subtitle?: string)}
	{@const alt = src.split('/').at(-1)}
	<div class="flex flex-col gap-2">
		<Image {src} {alt} class="rounded-xl" draggable="false" useViewer />
		{#if subtitle}
			<Badge class="rounded py-0">{subtitle}</Badge>
		{/if}
	</div>
{/snippet}

<div class="flex flex-col items-start gap-6">
	<span class="text-4xl font-bold">☁️ СберУниверситет / Медиатека</span>
	<span class="text-2xl font-extralight">
		Облачный сервис для сотрудников СберУниверситета, с помощью которого можно хранить и передавать
		коллегам файлы и папки, редактировать видео-контент.
	</span>
	{@render imgWithSubtitle(SberUniversityMain)}

	<div class="flex flex-col gap-4">
		<span class="text-4xl font-bold">Проект</span>
		<span class="text-xl font-extralight whitespace-pre-line">
			Задача заключалась в полном редизайне существующих решений и разработке нового функционала.
			Старая версия делалась без участия дизайнера, продумывания UX и компонентов.
		</span>
	</div>

	<div class="flex flex-col gap-4">
		<span class="text-4xl font-bold">Ролевая модель</span>
		<span class="text-xl font-extralight">
			<ol class="list-inside list-decimal">
				{#each ROLES_LIST as { title, description }, index (index)}
					<li class="marker: mt-1 font-bold">{title}</li>
					{description}
				{/each}
			</ol>
		</span>
	</div>

	<div class="flex flex-col gap-4">
		<span class="text-4xl font-bold">Процесс работы</span>
		<span class="text-xl font-extralight">
			<ul>
				{#each PROCESSES_LIST as process, index (index)}
					<li class="mt-1 ml-4">{process}</li>
				{/each}
			</ul>
		</span>
		<span class="text-xl font-extralight">
			<HighlightedText>
				В результате редизайна проблемных зон были сведены к минимуму задержки по выгрузке
				корпоративных материалов. Также, отслеживая метрику time on task, получили данные о
				сокращении времени на создание проекта с 11 мин до 6 мин
			</HighlightedText>
		</span>
	</div>

	<div class="flex flex-col gap-4">
		<span class="text-4xl font-bold">Мои задачи</span>
		<span class="text-xl font-extralight">
			<ul>
				{#each JOBS_LIST as jobDone, index (index)}
					<li class="mt-1 ml-4">{jobDone}</li>
				{/each}
			</ul>
		</span>
	</div>

	<div class="flex flex-col gap-4">
		<span class="text-4xl font-bold">Примеры редизайна</span>

		{@render imgWithSubtitle(SberUniversityFlowExample1)}
		{@render imgWithSubtitle(SberUniversityFlowExample2)}
	</div>

	<div class="flex flex-col gap-4">
		<span class="text-4xl font-bold">Макеты</span>

		{@render imgWithSubtitle(
			SberUniversityFlowExample3,
			'Главная страница и форма создания проекта',
		)}
		{@render imgWithSubtitle(
			SberUniversityFlowExample4,
			'Файлы, загруженные мной и форма загрузки',
		)}
		{@render imgWithSubtitle(
			SberUniversityFlowExample5,
			'Страница спикера и форма создания нового',
		)}
		{@render imgWithSubtitle(SberUniversityFlowExample6, 'Теги и пустая страница')}
		{@render imgWithSubtitle(SberUniversityFlowExample7, 'Поиск и аналитика')}
	</div>

	<div class="flex flex-col gap-4">
		<span class="text-4xl font-bold">⚡️Итоги</span>
		<span class="text-xl font-extralight">
			<HighlightedText>
				Теперь у сотрудников СберУниверситета есть простой и безопасный доступ к медиаконтенту с
				возможностью систематизировать и передавать коллегам файлы и папки, многократно
				редактировать видео-контент, сохраняя измененные версии.
			</HighlightedText>
		</span>
	</div>
</div>
