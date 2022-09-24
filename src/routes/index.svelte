<script>
	import { fly, fade } from "svelte/transition";
	import { onMount } from "svelte";
	import _ from "lodash";

	import IndexHero from "$lib/component/IndexHero/index.svelte";
	
  import athalia from "./logo-athalia.png";
  import bustanul from "./logo-bustanulmakmur.png";
  import cahayabangsa from "./logo-cahayabangsa.png";
  import darmayudha from "./logo-darmayudha.jpg";
  import globalprestasi from "./logo-globalprestasi.png";
  import ipeka from "./logo-ipeka.png";
  import it from "./logo-it.png";
  import kalamkudus from "./logo-kalamkudus.jpg";
  import kharismabangsa from "./logo-kharismabangsa.png";
  import kosayu from "./logo-kosayu.png";
  import mawar from "./logo-mawarsharon.png";
  import penabur from "./logo-penabur.png";
  import petra from "./logo-petra.png";
  import pribadidepok from "./logo-pribadidepok.jpg";
  import raffles from "./logo-raffles.jpg";
  import rajawali from "./logo-rajawali.jpg";
  import bintanglaut from "./logo-plbintang.png";
  import skinnyboi from "./skinnyboiv1.png";
  import witama from "./logo-witama.jpg";
  import malang from "./logo-1malang.png";
  import xaverius from "./logo-xaverius.jpg";
	import bee from "./tightboi.png";
	
  const participants = [

  	{// 0
		code: "MATEMATIKA",
		names: ["PENGUMUMAN FINAL"],
		school: "BRILLIANT COMPETITION XIV",
		insignia: skinnyboi,
	},

	{ // 6
      code: "M009",
      names: ["PERINGKAT 6", "Temporary"],
      school: "Temporary school",
      insignia: witama,
    },
	
	{ // 5
      code: "M009",
      names: ["JUARA 5", "Kenzo Alvaro Lim"],
      school: "SMP Witama Nasional Plus",
      insignia: witama,
    },

    { // 4
      code: "M009",
      names: ["JUARA 4", "Kenzo Alvaro Lim"],
      school: "SMP Witama Nasional Plus",
      insignia: witama,
    },

    { // 3
      code: "M024",
      names: ["JUARA 3", "Daffa Atha Arkana"],
      school: "MTsN 1 Kota Malang",
      insignia: malang,
    },

    { // 2
      code: "M031",
      names: ["JUARA 2", "Franklin Filbert"],
      school: "SMP Witama Nasional",
      insignia: witama,
    },

    { // 1
      code: "M045",
      names: ["JUARA 1", "Neilson Huang"],
      school: "SMP Darma Yudha",
      insignia: darmayudha,
    },
	];

	const winners = [participants[0], participants[1], participants[2], participants[3], participants[4],participants[5], participants[6]];
	let shownWinners = [];

	let shown = _.head(participants);
	let halted = false;

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
							<div in:fly={{y: 50, duration: 250 }}>
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
				<div class="mt-8 w-full flex-grow max-w-xl mx-auto p-2">
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
					class="block w-full mt-4 h-2 max-w-xl mx-auto bg-lavender rounded shadow p-4"
				/>
			</div>
		</div>
	</div>
</div>
