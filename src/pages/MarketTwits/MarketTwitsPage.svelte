<script lang="ts">
	import Badge from '$components/Badge.svelte';
	import HighlightedText from '$components/HighlightedText.svelte';
	import Image from '$components/Image.svelte';
	import Link from '$components/Link.svelte';
	import MarketTwitsFlowExample1 from '$images/MarketTwits/MarketTwitsFlowExample1.webp';
	import MarketTwitsFlowExample2 from '$images/MarketTwits/MarketTwitsFlowExample2.webp';
	import MarketTwitsFlowExample3 from '$images/MarketTwits/MarketTwitsFlowExample3.webp';
	import MarketTwitsFlowExample4 from '$images/MarketTwits/MarketTwitsFlowExample4.webp';
	import MarketTwitsFlowExample5 from '$images/MarketTwits/MarketTwitsFlowExample5.webp';
	import MarketTwitsFlowExample6 from '$images/MarketTwits/MarketTwitsFlowExample6.webp';
	import MarketTwitsFlowExample7 from '$images/MarketTwits/MarketTwitsFlowExample7.webp';
	import MarketTwitsJobStories from '$images/MarketTwits/MarketTwitsJobStories.webp';
	import MarketTwitsMain from '$images/MarketTwits/MarketTwitsMain.webp';

	const JOBS_LIST = [
		'Разработала информационную архитектуру с нуля',
		'Спроектировала пользовательские сценарии',
		'Спроектировала веб-интерфейс сервиса',
		'Взаимодействовала с разработчиками. В частности с back-end, так как были нюансы, связанные с парсингом новостей',
		'Постоянно общалась с техлидом для выяснения технических ограничений',
		'Выявляла и анализировала потребности аудитории с помощью глубинных интервью с респондентами',
		'Взаимодействовала с руководителем проекта для определения ключевых функциональных требований',
		'Презентовала и защищала свои решения стейкхолдеру и команде',
		'Собрала небольшую дизайн-систему на токенах для светлой и темной темы',
		'Проводила дизайн-ревью на тестовом стенде с фронтами до релиза после передачи макетов и после их реализации',
	];

	const SOURCES_LIST = [
		'внешние ресурсы, которые распределены по категориям и подкатегориям;',
		'другие пользователи сервиса, которые постят в свои ленты.',
	];
	const WIDGET_AVAILABLE_LIST = [
		'редактирование содержимого через настройки',
		'добавление и удаление ключевых слов без перехода в настройки',
		'закреп новостей',
		'перевод новости с английского языка',
		'редирект на источник',
		'возможность поделиться новостью с другими пользователями в чатах',
		'увидеть, если новость была отредактирована после публикции',
	];
</script>

{#snippet imgWithSubtitle(src: string, subtitle?: string)}
	{@const alt = src.split('/').at(-1)}
	<div class="flex flex-col gap-2" draggable="false">
		<Image {src} {alt} class="rounded-xl" useViewer />
		<Badge class="rounded py-0">{subtitle}</Badge>
	</div>
{/snippet}

<div class="flex flex-col items-start gap-6">
	<span class="text-4xl font-bold">🌐 MarketTwits / Новостной агрегатор</span>
	<span class="text-2xl font-extralight">
		Новостной агрегатор для трейдеров, использующих стратегию торговли на новостях.
	</span>
	<span class="text-xl font-extralight">
		ℹ️ <span class="italic">
			Это стратегия, при которой трейдеры используют влияние новостей и событий на рынке для
			принятия торговых решений
		</span>
	</span>
	{@render imgWithSubtitle(MarketTwitsMain, 'Рабочий стол')}

	<div class="flex flex-col gap-4">
		<span class="text-4xl font-bold">Проект</span>
		<span class="text-xl font-extralight">
			Идея клиента заключалась в создании продукта, который в рамках одной рабочей области собирал
			бы все необходимые открытые новостные источники с гибкими настройками и персонализацией. А так
			же со встроенным мессенджером, экономическим календарем, лентой пользователей, заметками,
			трансляциями и центром уведомлений. Работа велась над MVP версией продукта.
		</span>
	</div>

	<div class="flex flex-col gap-4">
		<span class="text-4xl font-bold">Job stories</span>
		<Image src={MarketTwitsJobStories} alt="MarketTwitsJobStories" draggable="false" useViewer />
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

	<div class="flex flex-col gap-6">
		<span class="text-4xl font-bold">Пример флоу</span>

		{@render imgWithSubtitle(MarketTwitsFlowExample1, 'Добавление новостного виджета')}
		<span class="text-xl font-extralight">
			Рабочий стол формируется из виджетов разного типа, некоторые из которых можно добавлять в
			неограниченном количестве, в первую очередь – новостной виджет. Добавление осуществляется
			через кнопку со списком.
		</span>

		{@render imgWithSubtitle(
			MarketTwitsFlowExample2,
			'Модальное окно с настройками новостного виджета',
		)}
		<span class="text-xl font-extralight whitespace-pre-line">
			{`В модальном окне предлагается заполнить название виджета, выбрать ключевые слова и новостные
			источники. Ключевые слова – биржевые тикеры, по которым будут фильтроваться новости из
			выбранных источников.
            
            Есть два типа источников:`}
			<ul>
				{#each SOURCES_LIST as source, index (index)}
					<li class="mt-1 ml-4">{source}</li>
				{/each}
			</ul>

			{`\nА также есть возможность самому добавить тг-каналы.
            Внешние ресурсы добавляет и модерирует админ.`}
		</span>

		{@render imgWithSubtitle(
			MarketTwitsFlowExample3,
			'Заполненный виджет. Из списка есть редирект на каждый источник.',
		)}

		{@render imgWithSubtitle(
			MarketTwitsFlowExample4,
			'Выбранные источники по каждой категории спрятаны в хинт.',
		)}

		{@render imgWithSubtitle(
			MarketTwitsFlowExample5,
			'Выбор пользователей в качестве новостного источника.',
		)}

		{@render imgWithSubtitle(
			MarketTwitsFlowExample6,
			'Добавление тг-канала. Он также вложен в категорию.',
		)}

		{@render imgWithSubtitle(MarketTwitsFlowExample7, 'Новостной виджет')}

		<span class="text-xl font-extralight whitespace-pre-line">
			Что доступно пользователям в созданном виджете:
			<ul>
				{#each WIDGET_AVAILABLE_LIST as source, index (index)}
					<li class="mt-1 ml-4">{source}</li>
				{/each}
			</ul>
			{``}
			Таким образом, новостной виджет позволяет одновременно считывать максимальное количество новостей
			из разных источников на одном экране, иметь гибкую персонализацию через добавление категорий новостей
			и выбор любых открытых источников (сайты, тг-каналы) с фильтрацией по ключевым словам.
		</span>

		<div class="flex flex-col gap-6">
			<span class="text-4xl font-bold">Проблемы, с которыми столкнулась и их решение</span>

			<div class="flex flex-col gap-3">
				<Badge class="rounded bg-pink-950 py-0 text-xl text-pink-400 opacity-80">Первая</Badge>
				<span class="text-xl font-extralight">
					Это был для меня вызов. Ранее я не сталкивалась со стартапами и с подобной спецификой.
					Первое время работа вынуждено велась без руководителя проекта, справлялись в паре с
					техлидом в ключевых вопросах. Их возникало очень много,
					<HighlightedText>
						решали регулярными встречами с клиентом и иногда его коллегами.
					</HighlightedText>
				</span>
			</div>

			<div class="flex flex-col gap-3">
				<Badge class="rounded bg-pink-950 py-0 text-xl text-pink-400 opacity-80">Вторая</Badge>
				<span class="text-xl font-extralight">
					Из функциональных требований была только общая идея продукта, и из-за специфики все
					органичения выяснялись по ходу. Не весь флоу был вовремя и достаточно прояснен, из-за чего
					иногда приходилось переделывать часть экранов и некоторая работа делалась «в стол».
					<HighlightedText>
						В качестве решения прорабатывала итерации флоу подробнее и чаще встречались с клиентом и
						командой для обсуждения.
					</HighlightedText>
				</span>
			</div>

			<div class="flex flex-col gap-3">
				<Badge class="rounded bg-pink-950 py-0 text-xl text-pink-400 opacity-80">Третья</Badge>
				<span class="text-xl font-extralight">
					Количество технических тонкестей и нюансов при разработке продукта сильно увеличили
					трудозатраты проекта и, к сожалению, клиентом было принято решение о заморозке проекта.
				</span>
			</div>

			<Link
				href="https://www.figma.com/design/ZEWyexvZit7iEDZnfw9Ool/MarketTwits-(Copy)?node-id=1041-4520&t=uie1kpKMZuZKRhPb-1"
				target="_blank"
				class="rounded-xl bg-blue-950 p-4 text-xl text-blue-300 opacity-80 hover:-translate-y-0.5 active:-translate-y-0.5 transition-all shadow hover:shadow-blue-600 active:shadow-blue-600"
			>
				🔗 Ссылка на фигму
			</Link>
		</div>
	</div>
</div>
