<script lang="ts">
	import Badge from '$components/Badge.svelte';
	import HighlightedText from '$components/HighlightedText.svelte';
	import Image from '$components/Image.svelte';
	import Link from '$components/Link.svelte';
	import TexolFlowExample1 from '$lib/assets/Texol/TexolFlowExample1.webp';
	import TexolFlowExample2 from '$lib/assets/Texol/TexolFlowExample2.webp';
	import TexolFlowExample3 from '$lib/assets/Texol/TexolFlowExample3.webp';
	import TexolFlowExample4 from '$lib/assets/Texol/TexolFlowExample4.webp';
	import TexolMain from '$lib/assets/Texol/TexolMain.webp';

	const JOBS_LIST = [
		'Спроектировала приложение для с нуля для внутренних сотрудников с ролевой моделью',
		'Взаимодействовала с разработчиками (фронт, бэк)',
		'Взаимодействовла с руководителем проекта и стейкхолдерами для выявления всех бизнес-требований',
		'Презентовала и защищала свои решения стейкхолдерам',
		'Для разработки UI использовала Material Design 3, дополняя компонентами',
	];

	const PROCESSES_LIST = [
		'После получения задачи, я принялась изучать документацию и функциональные требования',
		'Подготовила список вопросов для интервью со стейкхолдерами',
		'На интервью прояснила основной запрос по функционалу, уточнила важные детали и занялась ресерчем',
		'Проанализировав механики в смежных областях, собрала первую итерацию прототипов',
		'Презентовала их стейкхолдерам и согласовала проведение юзабилити-тестирования с 2-мя респондентами',
		'Проанализировала результаты тестов, внесла правки в основной флоу, согласовала решения со стейкхолдерами, приступила к сборке UI',
		'После согласования подготовила макеты к разработке',
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
	<span class="text-4xl font-bold">🛠️ Цифровой инспектор</span>
	<span class="text-2xl font-extralight">
		Корпоративное мобильное приложение для проверки вагонов-цистерн до и после налива
		нефтепродуктов.
	</span>
	{@render imgWithSubtitle(TexolMain)}

	<div class="flex flex-col gap-4">
		<span class="text-4xl font-bold">Проект</span>
		<span class="text-xl font-extralight whitespace-pre-line">
			Сотрудники – бригадиры, слесари и вагонники, обслуживающие вагоны-цистерны, работают на
			воздухе в любое время дня и ночи и в любую погоду. Все данные им приходилось фиксировать на
			бумаге.
			{``}
			Чтобы облегчить жизнь работникам и оптимизировать процесс проверки вагонов, было разработано корпоративное
			мобильное приложение Цифровой инспектор. Приложение автоматизирует проверку вагонов-цистерн до и
			после налива нефтепродуктов.
		</span>
	</div>

	<div class="flex flex-col gap-4">
		<span class="text-4xl font-bold">Мои задачи</span>
		<span class="text-xl font-extralight">
			{#each JOBS_LIST as jobDone, index (index)}
				<li class="mt-1 ml-4">{jobDone}</li>
			{/each}
		</span>
	</div>

	<div class="flex flex-col gap-4">
		<span class="text-4xl font-bold">Процесс работы</span>
		<span class="text-xl font-extralight">
			{#each PROCESSES_LIST as process, index (index)}
				<li class="mt-1 ml-4">{process}</li>
			{/each}
		</span>
		<span class="text-xl font-extralight">
			<HighlightedText>
				В результате цифровизации рабочего процесса полевых сотрудников среднее время на
				инспектирование одного вагона (метрика time on task) сократилось с 2 ч 20 мин до 1 ч 5 мин
				(был произведен нулевой замер)
			</HighlightedText>
		</span>
	</div>

	<div class="flex flex-col gap-4">
		<span class="text-4xl font-bold">⚡️Итоги</span>
		<span class="text-xl font-extralight">
			<li class="mt-1 ml-4">
				<span class="text-xl font-extralight">
					Теперь проверка вагонов-цистерн происходит
					<HighlightedText>в 2 раза быстрее</HighlightedText>
				</span>
			</li>
			<li class="mt-1 ml-4">
				<span class="text-xl font-extralight">
					<HighlightedText>Убытки компании сократились на 57%</HighlightedText>
					после автоматизации работы полевых сотрудников. Это произошло за счет сокращения простоев техники
					и числа ошибок, связанных с человеческим фактором
				</span>
			</li>
			<li class="mt-1 ml-4">
				<span class="text-xl font-extralight">
					<HighlightedText>На 146% повысилась прозрачность</HighlightedText>
					производственных процессов
				</span>
			</li>
		</span>
		<Link
			href="https://www.figma.com/design/RzZ75RykZXqkDX7pxu5CkE/Цифровой-инспектор?node-id=1-7306&t=a1ZQ4sCs6nTd1PBF-1"
			target="_blank"
			class="my-4 rounded-xl bg-blue-950 p-4 text-xl text-blue-300 opacity-80 hover:-translate-y-0.5 transition-all shadow hover:shadow-blue-600"
		>
			🔗 Ссылка на фигму
		</Link>

		{@render imgWithSubtitle(TexolFlowExample1, 'Аккаунт бригадира')}
		{@render imgWithSubtitle(TexolFlowExample2, 'Чек-лист')}
		{@render imgWithSubtitle(TexolFlowExample3, 'Замена ЗПА')}
		{@render imgWithSubtitle(TexolFlowExample4, 'Замена RFID-метки')}
	</div>
</div>
