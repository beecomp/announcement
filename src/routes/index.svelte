<script>
	import { fly, fade } from "svelte/transition";
	import { onMount } from "svelte";
	import _ from "lodash";

	import IndexHero from "$lib/component/IndexHero/index.svelte";
	
  import athalia from "./logo-athalia.png";
  import darmayudha from "./logo-darmayudha.png";
  import penabur from "./logo-penabur.png";
  import kebayoran from "./logo-kebayoran.png";
  import insanharapan from "./logo-insanharapan.png";
  import bintanglaut from "./logo-plbintang.png";
  import rajawali from "./logo-katolikrajawali.png";
  import witama from "./logo-witama.png";
  import malang from "./logo-1malang.png";
  import xaverius from "./logo-xaverius.png";
  import kharismabangsa from "./logo-kharismabangsa.jpg";
  import kristenkanaan from "./logo-kristenkanaan.png";
  import PL from "./logo-pangudiluhur.png";
  import TB from "./logo-tarunabangsa.png";
  import ipeka from "./logo-ipeka.png";
	import bee from "./tightboi.png";
	
  const participants = [

	 {  
     code: "S012",
     names: ["Helena Subrata", "Audrey Vallerie Riady"],
	 school: "SMPK PENABUR GADING SERPONG",
     insignia: penabur,
     },
     {  
       code: "S016",
       names: ["Felicia Ivana Yuval", "Benjamin Hutapea"],
       school: "SMPK 7 Penabur Jakarta",
       insignia: penabur,
     },
     {  
       code: "S017",
       names: ["Davino Sugianto", "Devin Cahyadi"],
       school: "SMPK 7 PENABUR JAKARTA",
       insignia: penabur,
     },
     { 
       code: "S019",
       names: ["Felicia Lovina Cuaca", "Ruben Valentino Rasoki Pardede"],
       school: "SMP Kristen Kanaan Banjarmasin",
       insignia: kristenkanaan,
     },
     { 
       code: "S023",
       names: ["Michell Alicia"],
       school: "SMPK Penabur Kota Modern",
       insignia: penabur,
     },
     {  
       code: "S025",
       names: ["Jeremias Shalomoses Simangunsong", "Keiko Maxwell"],
       school: "SMPK BPK Penabur Singgasana",
       insignia: penabur,
     },
     {  
       code: "S027",
       names: ["Bagasmora Andreo Sibarani", "Mikhael Faith Benaiah Liveroy Saragih"],
       school: "SMP Darma Yudha",
       insignia: darmayudha,
     },
     { 
       code: "S032",
       names: ["Samuel Tan", "Wesley Adrian Laurance"],
       school: "Sekolah Athalia",
       insignia: athalia,
     },
     {  
       code: "S034",
       names: ["Dzakwan Alvaro Putra Yudana", "Fariz Rayyan Firdaus"],
       school: "Kharisma Bangsa",
       insignia: kharismabangsa,
     },
     {
    	code: "S036",
       names: ["Kaleb Iash Elnathan Naibaho", "Cokorda Bagus Satria Adijaya"],
       school: "SMP Pangudi Luhur Jakarta",
       insignia: PL,
     },
     {  
       code: "S040",
       names: ["Cheryll Adeline Saputra", "Darren Kenzie"],
       school: "SMPK 1 BPK PENABUR Bandung",
       insignia: penabur,
     },
     {  
       code: "S044",
       names: ["Gede Panji Gelgel Wiradarma", "Maudry Viriya Prawira"],
       school: "SMP Taruna Bangsa",
       insignia: TB,
     },
     {  
       code: "S046",
       names: ["Sulthan Maulana Akbar Nasution", "Mika Farees Anwar"],
       school: "SMP Labschool Kebayoran",
       insignia: kebayoran,
     },
	  {  
       code: "S048",
       names: ["RANUGUNAR SAVAHASTA", "VANIA MARISSA FAYOLA RITONGA"],
       school: "SMP LABSCHOOL KEBAYORAN",
       insignia: kebayoran,
     },
	  { 
       code: "S050",
       names: ["Elliana Gracia Davina Harwinanto", "Daniel Surya Chandra"],
       school: "SMPK 2 PENABUR JAKARTA",
       insignia: penabur,
     },
	];

	const winners = [participants[0], participants[1], participants[4], participants[3], participants[2], participants[5], participants[6],participants[7], participants[8], participants[9], participants[10], participants[11], participants[12], participants[13], participants[14], participants[15]];
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
