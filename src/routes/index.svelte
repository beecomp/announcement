<script>
	import { fly, fade } from "svelte/transition";
	import { onMount } from "svelte";
	import _ from "lodash";

	import IndexHero from "$lib/component/IndexHero/index.svelte";

  import athalia from "./logo-athalia.png";
  import cahayarancamaya from "./logo-cahayarancamaya.jpg";
  import darmayudha from "./logo-darmayudha.jpg";
  import globalprestasi from "./logo-globalprestasi.png";
  import tarki3 from "./logo-tarki.jpg";
  import ipeka from "./logo-ipeka.png";
  import kalamkudus from "./logo-kalamkudus.jpg";
  import ketapang from "./logo-ketapang.png";
  import kharismabangsa from "./logo-kharismabangsa.png";
  import marsudirini from "./logo-marsudirini.jpg";
  import penabur from "./logo-penabur.png";
  import petra from "./logo-petra.png";
  import rajawali from "./logo-rajawali.jpg";
  import santalaurensia from "./logo-santalaurensia.png";
  import santoaloysius from "./logo-santoaloysius.jpeg";
	import bee from "./skinnyboiv1.png";

	const participants = [
    {
      code: "S001",
      names: ["Baruna Adi Sanjaya, Narendra Aditya Tanoto"],
      school: "SMP Cahaya Rancamaya",
      insignia: tarki3,
    },

    { 
      code: "S011",
      names: ["Stevenson Christopher Hudiono, Cheerish Natalia Rifel"],
      school: "SMPK 2 Penabur",
      insignia: penabur,
    },

    {
      code: "S020",
      names: ["Felix Halley Thamin, Gratia Plena Kusdevina"],
      school: "SMPK 4 Penabur",
      insignia: penabur,
    },

    { 
      code: "S027",
      names: ["Jack Howard Wijaya, Juan Howard Wijaya"],
      school: "SMP Darma Yudha Pekanbaru",
      insignia: darmayudha,
    },
    
    {
      code: "S030",
      names: ["Nathan Raphael Martua N., William Tengganu"],
      school: "SMP Global Prestasi",
      insignia: globalprestasi,
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
