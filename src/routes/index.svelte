<script>
	import { fly, fade } from "svelte/transition";
	import { onMount } from "svelte";
	import _ from "lodash";

	import IndexHero from "$lib/component/IndexHero/index.svelte";

  import malang from "./logo-1malang.png";
  import jakarta4 from "./logo-4jakarta.png";
  import jakarta41 from "./logo-41jakarta.png";
  import alittihad from "./logo-allitihad.png";
  import athalia from "./logo-athalia.png";
  import balikpapan from "./logo-balikpapan.png";
  import banyuwangi from "./logo-banyumangi.png";
  import bogorraya from "./logo-bogorraya.png";
  import darmayudha from "./logo-darmayudha.png";
  import depok from "./logo-depok.png";
  import dianharapan from "./logo-dianharapan.png";
  import insan from "./logo-insan.png";
  import insanharapan from "./logo-insanharapan.png";
  import insanparepare from "./logo-insanparepare.png";
  import ipeka from "./logo-ipeka.png";
  import kalamkhudus from "./logo-kalamkhudus.png";
  import katolikrajawali from "./logo-katolikrajawali.png";
  import katoliksantaclara from "./logo-katoliksantaclara.png";
  import kebayoran from "./logo-kebayoran.png";
  import kharismabangsa from "./logo-kharismabangsa.png";
  import kristenkenaan from "./logo-kristenkenaan.png";
  import lamongan from "./logo-lamongan.png";
  import maitreyawira from "./logo-maitreyawira.png";
  import mentari from "./logo-mentari.png";
  import mondial from "./logo-mondial.png";
  import pahoa from "./logo-pahoa.png";  
  import pangudiluhur from "./logo-pangudiluhur.png";
  import penabur from "./logo-penabur.png";  
  import pilarbangsa from "./logo-pilarbangsa.png";
  import plbintang from "./logo-plbintang.png";  
  import saintjohn from "./logo-saintjohn.png";
  import stellamaris from "./logo-stellamaris.png";  
  import strada from "./logo-strada.png";
  import tarakanita from "./logo-tarakanita.png";  
  import tarunabangsa from "./logo-tarunabangsa.png";
  import tunasbangsa from "./logo-tunasbangsa.png";  
  import witama from "./logo-witama.png";
  import xaverius from "./logo-xaverius.png";

	const participants = [
    {
      code: "S001",
      names: ["Baruna Adi Sanjaya, Narendra Aditya Tanoto"],
      school: "SMP Cahaya Rancamaya",
      insignia: tarakanita,
    },

  ];

	const winners = [participants[2], participants[4], participants[0], participants[1], participants[3]];
	let shownWinners = [];

	let shown = _.head(participants);
	let halted = false;
	onMount(() => {
		const interval = setInterval(() => {
			if (halted) return;
			let next = shown;
			while (next == shown || shownWinners.includes(next)) {
				next = _.sample(participants);
			}
			shown = next;
		}, 250);
	});

	const magic = () => {
		if (halted && shownWinners.length == winners.length) return;
		if (halted) return (halted = false);
		halted = true;
		shown = winners[shownWinners.length];
		shownWinners = [shown, ...shownWinners];
	};
</script>

<svelte:head>
	<title>Announcement · Brilliant Competition</title>
</svelte:head>

<div class="flex flex-col h-full">
	<IndexHero />
	<div class="mt-8 flex-grow">
		<div class="container mx-auto h-full">
			<div class="flex flex-col h-full p-12 max-w-7xl px-4 sm:px-6 lg:px-8 mx-auto">
				<div class="flex space-x-16">
					{#key shown}
						<div in:fly={{ y: 25, duration: 250 }} class="bg-white rounded-lg shadow-lg p-4 z-10">
							<img
								class="h-[20rem] min-h-[20rem] w-[20rem] min-w-[20rem] object-contain"
								src={shown.insignia}
								alt="school logo"
							/>
						</div>
					{/key}

					<div class="flex flex-col">
						{#key shown}
							<div in:fly={{ delay: 100, y: 50, duration: 250 }}>
								<div class="text-white text-5xl font-montserrat break-words">
									{shown.names[0]}
								</div>
								{#if shown.names[1]}
									<div class="mt-8 text-white text-5xl font-montserrat break-words">
										{shown.names[1]}
									</div>
								{/if}
								<div class="text-white text-3xl italic font-montserrat break-words">
									{shown.code}
								</div>
							</div>
						{/key}
						<div class="flex-grow" />
						{#key shown}
							<div in:fly={{ y: 20, duration: 250 }}>
								<div class="text-white text-4xl font-montserrat break-words">
									{shown.school}
								</div>
							</div>
						{/key}
					</div>
				</div>
				<div class="mt-8 w-full flex-grow max-w-xl mx-auto p-4">
					<ul class="font-barlow-semi text-white text-l space-y-1">
						{#each _.take(shownWinners, 6) as t}
							<li class="text-center">
								{t.code} &nbsp;&nbsp;|&nbsp;&nbsp; {t.names.join(" - ")}
							</li>
						{/each}
					</ul>
				</div>
				<button
					on:click={() => magic()}
					class="block w-full mt-4 h-2 max-w-2xl mx-auto bg-lavender rounded shadow p-4"
				/>
			</div>
		</div>
	</div>
</div>
