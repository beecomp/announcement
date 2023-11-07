<script>
	import _ from "lodash";
	import { onMount } from "svelte";
	import { fade, fly } from "svelte/transition";

	import IndexHero from "$lib/component/IndexHero/index.svelte";
	
  import bee2024 from "./bee2024.png";
  import malang from "./logo-1malang.png";
  import athalia from "./logo-athalia.png";
  import darmayudha from "./logo-darmayudha.png";
  import insanharapan from "./logo-insanharapan.png";
  import ipeka from "./logo-ipeka.png";
  import rajawali from "./logo-katolikrajawali.png";
  import kebayoran from "./logo-kebayoran.png";
  import kharismabangsa from "./logo-kharismabangsa.jpg";
  import kristenkanaan from "./logo-kristenkanaan.png";
  import PL from "./logo-pangudiluhur.png";
  import penabur from "./logo-penabur.png";
  import bintanglaut from "./logo-plbintang.png";
  import TB from "./logo-tarunabangsa.png";
  import witama from "./logo-witama.png";
  import xaverius from "./logo-xaverius.png";
  import skinnyboi from "./skinnyboiv1.png";
  import bee from "./tightboi.png";
	
  const participants = [

	{ // 0
		code: "SCIENCE",
		names: ["PENGUMUMAN FINAL"],
		school: "BRILLIANT COMPETITION XIV",
		insignia: bee2024,
	},

	{  // 1
		code: "BIDANG SCIENCE",
		names: ["", "PERINGKAT 6"],
		school: "BRILLIANT COMPETITION XIV",
		insignia: bee2024,
	},

	{  // 2
		code: "S040",
		names: ["PERINGKAT 6", "Cheryll Adeline Saputra, Darren Kenzie"],
		school: "SMPK 1 BPK PENABUR Bandung",
		insignia: penabur,
	},

	{  // 3
		code: "BIDANG SCIENCE",
		names: ["", "JUARA 5"],
		school: "BRILLIANT COMPETITION XIV",
		insignia: bee2024,
	},

	{  // 4
		code: "S046",
		names: ["JUARA 5", "Sulthan Maulana Akbar Nasution, Mika Farees Miswar"],
		school: "SMP Labschool Kebayoran",
		insignia: kebayoran,
	},

	{  // 5
		code: "BIDANG SCIENCE",
		names: ["", "JUARA 4"],
		school: "BRILLIANT COMPETITION XIV",
		insignia: bee2024,
	},

	{ // 6
		code: "S025",
		names: ["JUARA 4", "Jeremias Shalomoses Simangunsong, Keiko Maxwell"],
		school: "SMPK BPK Penabur Singgasana",
		insignia: penabur,
	},

	{  // 7
		code: "BIDANG SCIENCE",
		names: ["", "JUARA 3"],
		school: "BRILLIANT COMPETITION XIV",
		insignia: bee2024,
	},

	{ // 8
		code: "S017",
		names: ["JUARA 3", "Davino Sugianto, Devin Cahyadi"],
		school: "SMPK 7 PENABUR",
		insignia: penabur,
	},

	{  // 9
		code: "BIDANG SCIENCE",
		names: ["", "JUARA 2"],
		school: "BRILLIANT COMPETITION XIV",
		insignia: bee2024,
	},

	{ // 10
		code: "S050",
		names: ["JUARA 2", "Elliana Gracia Davina Harwinanto, Daniel Surya Chandra"],
		school: "SMPK 2 PENABUR",
		insignia: penabur,
	},

	{  // 11
		code: "BIDANG SCIENCE",
		names: ["", "JUARA 1"],
		school: "BRILLIANT COMPETITION XIV",
		insignia: bee2024,
	},

	{  // 12
		code: "S027",
		names: ["JUARA 1", "Bagasmora Andreo Sibarani, Mikhael Faith Benaiah Liveroy Saragih"],
		school: "SMP Darma Yudha",
		insignia: darmayudha,
	},
];

	const schools = [
		{ // 0
			code: "",
			names: ["JUARA 4"],
			school: "SMP Darma Yudha",
			insignia: darmayudha,
		},

		{
			code: "",
			names: ["JUARA 5"],
			school: "SMPK 2 PENABUR",
			insignia: penabur,
		},
	];

	const winners = [participants[0], participants[3] , participants[4], participants[5], participants[6], participants[7], participants[8], participants[9], participants[10], participants[11], 
	participants[12], participants[1], participants[2]];
	let shownWinners = [];

	let shown = _.head(schools);
	let halted = false;
	onMount(() => {
		const interval = setInterval(() => {
			if (halted) return;
			let next = shown;
			while (next == shown || shownWinners.includes(next)) {
				next = _.sample(schools);
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
		<div class="">
			<div class="mt-8 flex-grow">
				<div class="container mx-auto h-full">
					<div class="flex flex-col h-full p-12 max-w-7xl px-4 sm:px-6 lg:px-8 mx-auto">
						<div class="flex space-x-16">
							{#key shown}
								<div in:fly={{ y: 25, duration: 250 }} class="">
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
										<div class="text-black text-5xl font-montserrat break-words">
											{shown.names[0]}
										</div>
										{#if shown.names[1]}
											<div class="mt-8 text-black text-5xl font-montserrat break-words">
												{shown.names[1]}
											</div>
										{/if}
										<div class="text-black text-3xl italic font-montserrat break-words">
											{shown.code}
										</div>
									</div>
								{/key}
								<div class="flex-grow" />
								{#key shown}
									<div in:fly={{ y: 20, duration: 250 }}>
										<div class="text-black text-4xl font-montserrat break-words">
											{shown.school}
										</div>
									</div>
								{/key}
							</div>
						</div>
						<div class="mt-8 w-full flex-grow max-w-xl mx-auto p-4">
							<ul class="font-barlow-semi text-black text-l space-y-1">
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
</div>
