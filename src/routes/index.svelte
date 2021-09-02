<script>
	import { fly, fade } from 'svelte/transition';
	import { onMount } from 'svelte';
	import _ from 'lodash';

	import IndexHero from '$lib/component/IndexHero/index.svelte';
	import school from './kalam-kudus.jpg';
	import bee from './tightboi.png';
	const participants = [
		{
			code: 'MAT-069',
			names: ['Otto Alexander Sutianto', 'William Leonard Sumendap'],
			school: 'SMP Kalam Kudus Solo',
			insignia: school
		},
		{
			code: 'MAT-420',
			names: ['Lebah Lebah Lebah', 'Buzz "Aldrin" Buzz'],
			school: 'SMP Kalam Kudus Solo',
			insignia: bee
		}
	];

	let shown = _.head(participants);
	onMount(() => {
		const interval = setInterval(() => {
			let next = _.sample(participants);
			while (next == shown) next = _.sample(participants);
			shown = next;
		}, 750);
	});
</script>

<svelte:head>
	<title>Announcement · Brilliant Competition</title>
</svelte:head>

<div class="flex flex-col h-full">
	<IndexHero />
	<div class="mt-8 flex-grow">
		<div class="container mx-auto">
			<div class="max-w-7xl px-4 sm:px-6 lg:px-8 mx-auto">
				<div class="flex space-x-16">
					<div class="bg-white rounded-lg shadow-lg p-4">
						{#key shown}
							<img
								in:fly={{ y: 25, duration: 250 }}
								class="h-[20rem] min-h-[20rem] w-[20rem] min-w-[20rem] object-contain"
								src={shown.insignia}
								alt="school logo"
							/>
						{/key}
					</div>

					<div class="flex flex-col">
						{#key shown}
							<div in:fly={{ y: 100, duration: 250 }}>
								<div class="text-gray-700 text-5xl font-montserrat break-words">
									{shown.names[0]}
								</div>
								{#if shown.names[1]}
									<div class="mt-8 text-gray-700 text-5xl font-montserrat break-words">
										{shown.names[1]}
									</div>
								{/if}
								<div class="text-gray-500 text-3xl italic font-montserrat break-words">MAT-069</div>
							</div>
						{/key}
						<div class="flex-grow" />
						{#key shown}
							<div in:fly={{ y: 35, duration: 250 }}>
								<div class="text-gray-700 text-4xl font-montserrat break-words">
									SMP Kalam Kudus Solo
								</div>
							</div>
						{/key}
					</div>
				</div>
				<div class="mt-8 max-w-2xl mx-auto bg-coral-light rounded shadow p-4">
					<ul class="font-barlow-semi text-gray-700 text-xl space-y-1">
						<li>
							MAT-001 &nbsp;&nbsp;|&nbsp;&nbsp; Otto Alexander Sutianto - William Leonard Sumendap
						</li>
						<li>
							MAT-001 &nbsp;&nbsp;|&nbsp;&nbsp; Otto Alexander Sutianto - William Leonard Sumendap
						</li>
						<li>
							MAT-001 &nbsp;&nbsp;|&nbsp;&nbsp; Otto Alexander Sutianto - William Leonard Sumendap
						</li>
						<li>
							MAT-001 &nbsp;&nbsp;|&nbsp;&nbsp; Otto Alexander Sutianto - William Leonard Sumendap
						</li>
						<li>
							MAT-001 &nbsp;&nbsp;|&nbsp;&nbsp; Otto Alexander Sutianto - William Leonard Sumendap
						</li>
						<li>
							MAT-001 &nbsp;&nbsp;|&nbsp;&nbsp; Otto Alexander Sutianto - William Leonard Sumendap
						</li>
					</ul>
				</div>
			</div>
		</div>
	</div>
</div>
