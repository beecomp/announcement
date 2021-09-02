<script>
	import IndexHero from '$lib/component/IndexHero/index.svelte';
	import school from './kalam-kudus.jpg';
	import tightboi from './tightboi.png';
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
						<img
							class="h-[20rem] min-h-[20rem] w-[20rem] min-w-[20rem] object-contain"
							src={school}
							alt="school logo"
						/>
					</div>

					<div class="flex flex-col">
						<div class="text-gray-700 text-5xl font-montserrat break-words">
							Otto Alexander Sutianto
						</div>
						<div class="mt-8 text-gray-700 text-5xl font-montserrat break-words">
							William Leonard Summendap
						</div>
						<div class="text-gray-500 text-3xl italic font-montserrat break-words">MAT-069</div>
						<div class="flex-grow" />
						<div class="text-gray-700 text-4xl font-montserrat break-words">
							SMP Kalam Kudus Solo
						</div>
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
