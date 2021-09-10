<script>
	import { fly, fade } from "svelte/transition";
	import { onMount } from "svelte";
	import _ from "lodash";

	import IndexHero from "$lib/component/IndexHero/index.svelte";

  import athalia from "./logo-athalia.png";
  import cahayarancamaya from "./logo-cahayarancamaya.jpg";
  import darmayudha from "./logo-darmayudha.jpg";
  import globalprestasi from "./logo-globalprestasi.png";
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
	import bee from "./tightboi.png";

	const participants = [
    { // 0
      code: "S001",
      names: ["Baruna Adi Sanjaya, Narendra Aditya Tanoto"],
      school: "SMP Cahaya Rancamaya",
      insignia: cahayarancamaya,
    },
    // { // 1
    //   code: "S003",
    //   names: ["Satya Virya Atmadja"],
    //   school: "SMPK Penabur Serang",
    //   insignia: penabur,
    // },
    // { // 2
    //   code: "S004",
    //   names: ["Felicia Putri Gondokusumo, Herbert Karsten Juwono"],
    //   school: "SMP Kristen Petra 3 Surabaya",
    //   insignia: petra,
    // },
    // { // 3
    //   code: "S005",
    //   names: ["Fariz Rayyan Firdaus, Dzakwan Alvaro Putra"],
    //   school: "SMP Kharisma Bangsa",
    //   insignia: kharismabangsa,
    // },
    // { // 4
    //   code: "S006",
    //   names: ["Abdullah Karim, Pradipto Pandu Maheswara"],
    //   school: "SMP Kharisma Bangsa",
    //   insignia: kharismabangsa,
    // },
    // { // 5
    //   code: "S009",
    //   names: ["Richard Huang"],
    //   school: "SMPK Penabur Gading Serpong",
    //   insignia: penabur,
    // },
    // { // 6
    //   code: "S010",
    //   names: ["Justin, Edward Eugene Surya"],
    //   school: "SMPK 2 Penabur",
    //   insignia: penabur,
    // },
    { // 7
      code: "S011",
      names: ["Stevenson Christopher Hudiono, Cheerish Natalia Rifel"],
      school: "SMPK 2 Penabur",
      insignia: penabur,
    },
    // { // 8
    //   code: "S012",
    //   names: ["Adriel Nathanael Winfryd, Krislyn W Riyadi"],
    //   school: "SMPK 7 Penabur",
    //   insignia: penabur,
    // },
    // { // 9
    //   code: "S013",
    //   names: ["Cynthia Nikita Wibowo, Jeremee Rafael Wynn"],
    //   school: "SMPK Penabur Kota Modern",
    //   insignia: penabur,
    // },
    // { // 10
    //   code: "S014",
    //   names: ["Welfrydus Winnersdy Rante, Tiara Siddhi Fonso"],
    //   school: "SMP Katolik Rajawali Makassar",
    //   insignia: rajawali,
    // },
    // { // 11
    //   code: "S015",
    //   names: ["Justin Benaya Tirtadjaja, Fellyta Aquila Chiandra"],
    //   school: "SMP Marsudirini Bogor",
    //   insignia: marsudirini,
    // },
    // { // 12
    //   code: "S016",
    //   names: ["Kenneth Nicander Wijaya, Stefani Angela"],
    //   school: "SMPK 6 Penabur",
    //   insignia: penabur,
    // },
    // { // 13
    //   code: "S017",
    //   names: ["Vanessa Natalie Karlina, Katharine Lauren Tie"],
    //   school: "SMP Santo Aloysius 2",
    //   insignia: santoaloysius,
    // },
    // { // 14
    //   code: "S018",
    //   names: ["Abigail Venus Rashando, Calysta Bernice Prasasti"],
    //   school: "SMP Santo Aloysius 2",
    //   insignia: santoaloysius,
    // },
    // { // 15
    //   code: "S019",
    //   names: ["Joshua Emmanuel Wahyu, Vania Feby Wijaya"],
    //   school: "SMPK 2 PENABUR",
    //   insignia: penabur,
    // },
    { // 16
      code: "S020",
      names: ["Felix Halley Thamin, Gratia Plena Kusdevina"],
      school: "SMPK 4 Penabur",
      insignia: penabur,
    },
    // { // 17
    //   code: "S022",
    //   names: ["Abraham Brandon Purnama"],
    //   school: "SMP Kristen Ketapang 1 Jakarta",
    //   insignia: ketapang,
    // },
    // { // 18
    //   code: "S023",
    //   names: ["Ethan Samuel Benaya Khu"],
    //   school: "SMPK Penabur Kota Modern",
    //   insignia: penabur,
    // },
    // { // 19
    //   code: "S025",
    //   names: ["Sammuel Lim, Anthony Christian"],
    //   school: "SMP Kristen IPEKA Puri",
    //   insignia: ipeka,
    // },
    { // 20
      code: "S027",
      names: ["Jack Howard Wijaya, Juan Howard Wijaya"],
      school: "SMP Darma Yudha Pekanbaru",
      insignia: darmayudha,
    },
    // { // 21
    //   code: "S028",
    //   names: ["Bagasmora Andreo Sibarani, Mikhael Faith Benaiah L. Saragih"],
    //   school: "SMP Darma Yudha Pekanbaru",
    //   insignia: darmayudha,
    // },
    // { // 22
    //   code: "S029",
    //   names: ["Khansky Khonery, Melvin Raphael Gandaatmaja"],
    //   school: "Santa Laurensia Junior High School",
    //   insignia: santalaurensia,
    // },
    { // 23
      code: "S030",
      names: ["Nathan Raphael Martua N., William Tengganu"],
      school: "SMP Global Prestasi",
      insignia: globalprestasi,
    },
    // { // 24
    //   code: "S031",
    //   names: ["Tsabitah Abiyyu, Joanna Stevia C."],
    //   school: "SMP Global Prestasi",
    //   insignia: globalprestasi,
    // },
    // { // 25
    //   code: "S032",
    //   names: ["Clara Christovia Sahetapy, Sevonarola Haryo Lumenta"],
    //   school: "SMP Athalia",
    //   insignia: athalia,
    // },
    // { // 26
    //   code: "S033",
    //   names: ["Feliska Adenia Lubitha, Cornelius Jabez Lim"],
    //   school: "SMP Athalia",
    //   insignia: athalia,
    // },
    // { // 27
    //   code: "S034",
    //   names: ["Matthew Christopher H, Kaitlyn Illian Toniman"],
    //   school: "SMPK Penabur Gading Serpong",
    //   insignia: penabur,
    // },
    // { // 28
    //   code: "S035",
    //   names: ["Gabriella Anna Santoso, Kayla Theodora Wibisana"],
    //   school: "SMPK Kelapa Gading",
    //   insignia: penabur,
    // },
    // { // 29
    //   code: "S036",
    //   names: ["Fiorine Audiera Han"],
    //   school: "SMPK PENABUR Kota Modern",
    //   insignia: penabur,
    // },
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
								<div class="text-gray-700 text-5xl font-montserrat break-words">
									{shown.names[0]}
								</div>
								{#if shown.names[1]}
									<div class="mt-8 text-gray-700 text-5xl font-montserrat break-words">
										{shown.names[1]}
									</div>
								{/if}
								<div class="text-gray-500 text-3xl italic font-montserrat break-words">
									{shown.code}
								</div>
							</div>
						{/key}
						<div class="flex-grow" />
						{#key shown}
							<div in:fly={{ y: 20, duration: 250 }}>
								<div class="text-gray-700 text-4xl font-montserrat break-words">
									{shown.school}
								</div>
							</div>
						{/key}
					</div>
				</div>
				<div class="mt-8 w-full flex-grow max-w-xl mx-auto p-4">
					<ul class="font-barlow-semi text-gray-700 text-l space-y-1">
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
