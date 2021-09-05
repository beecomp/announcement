<script>
	import { fly, fade } from "svelte/transition";
	import { onMount } from "svelte";
	import _ from "lodash";

	import IndexHero from "$lib/component/IndexHero/index.svelte";
	import school from "./kalam-kudus.jpg";
	import bee from "./tightboi.png";
	const participants = [
    {
      code: "S001",
      names: ["Baruna Adi Sanjaya, Narendra Aditya Tanoto"],
      school: "SMP Cahaya Rancamaya",
      insignia: bee,
    },
    {
      code: "S003",
      names: ["Satya Virya Atmadja"],
      school: "SMPK Penabur Serang",
      insignia: bee,
    },
    {
      code: "S004",
      names: ["Felicia Putri Gondokusumo, Herbert Karsten Juwono"],
      school: "SMP Kristen Petra 3 Surabaya",
      insignia: bee,
    },
    {
      code: "S005",
      names: ["Fariz Rayyan Firdaus, Dzakwan Alvaro Putra"],
      school: "SMP Kharisma Bangsa",
      insignia: bee,
    },
    {
      code: "S006",
      names: ["Abdullah Karim, Pradipto Pandu Maheswara"],
      school: "SMP Kharisma Bangsa",
      insignia: bee,
    },
    {
      code: "S009",
      names: ["Richard Huang"],
      school: "SMPK Penabur Gading Serpong",
      insignia: bee,
    },
    {
      code: "S010",
      names: ["Justin, Edward Eugene Surya"],
      school: "SMPK 2 Penabur",
      insignia: bee,
    },
    {
      code: "S011",
      names: ["Stevenson Christopher Hudiono, Cheerish Natalia Rifel"],
      school: "SMPK 2 Penabur",
      insignia: bee,
    },
    {
      code: "S012",
      names: ["Adriel Nathanael Winfryd, Krislyn W Riyadi"],
      school: "SMPK 7 Penabur",
      insignia: bee,
    },
    {
      code: "S013",
      names: ["Cynthia Nikita Wibowo, Jeremee Rafael Wynn"],
      school: "SMPK Penabur Kota Modern",
      insignia: bee,
    },
    {
      code: "S014",
      names: ["Welfrydus Winnersdy Rante, Tiara Siddhi Fonso"],
      school: "SMP Katolik Rajawali Makassar",
      insignia: bee,
    },
    {
      code: "S015",
      names: ["Justin Benaya Tirtadjaja, Fellyta Aquila Chiandra"],
      school: "SMP Marsudirini Bogor",
      insignia: bee,
    },
    {
      code: "S016",
      names: ["Kenneth Nicander Wijaya, Stefani Angela"],
      school: "SMPK 6 Penabur",
      insignia: bee,
    },
    {
      code: "S017",
      names: ["Vanessa Natalie Karlina, Katharine Lauren Tie"],
      school: "SMP Santo Aloysius 2",
      insignia: bee,
    },
    {
      code: "S018",
      names: ["Abigail Venus Rashando, Calysta Bernice Prasasti"],
      school: "SMP Santo Aloysius 2",
      insignia: bee,
    },
    {
      code: "S019",
      names: ["Joshua Emmanuel Wahyu, Vania Feby Wijaya"],
      school: "SMPK 2 PENABUR",
      insignia: bee,
    },
    {
      code: "S020",
      names: ["Felix Halley Thamin, Gratia Plena Kusdevina"],
      school: "SMPK 4 Penabur",
      insignia: bee,
    },
    {
      code: "S022",
      names: ["Abraham Brandon Purnama"],
      school: "SMP Kristen Ketapang 1 Jakarta",
      insignia: bee,
    },
    {
      code: "S023",
      names: ["Ethan Samuel Benaya Khu"],
      school: "SMPK Penabur Kota Modern",
      insignia: bee,
    },
    {
      code: "S025",
      names: ["Sammuel Lim, Anthony Christian"],
      school: "SMP Kristen IPEKA Puri",
      insignia: bee,
    },
    {
      code: "S027",
      names: ["Jack Howard Wijaya, Juan Howard Wijaya"],
      school: "SMP Darma Yudha Pekanbaru",
      insignia: bee,
    },
    {
      code: "S028",
      names: ["Bagasmora Andreo Sibarani, Mikhael Faith Benaiah L. Saragih"],
      school: "SMP Darma Yudha Pekanbaru",
      insignia: bee,
    },
    {
      code: "S029",
      names: ["Khansky Khonery, Melvin Raphael Gandaatmaja"],
      school: "Santa Laurensia Junior High School",
      insignia: bee,
    },
    {
      code: "S030",
      names: ["Nathan Raphael Martua N., William Tengganu"],
      school: "SMP Global Prestasi",
      insignia: bee,
    },
    {
      code: "S031",
      names: ["Tsabitah Abiyyu, Joanna Stevia C."],
      school: "SMP Global Prestasi",
      insignia: bee,
    },
    {
      code: "S032",
      names: ["Clara Christovia Sahetapy, Sevonarola Haryo Lumenta"],
      school: "SMP Athalia",
      insignia: bee,
    },
    {
      code: "S033",
      names: ["Feliska Adenia Lubitha, Cornelius Jabez Lim"],
      school: "SMP Athalia",
      insignia: bee,
    },
    {
      code: "S034",
      names: ["Matthew Christopher H, Kaitlyn Illian Toniman"],
      school: "SMPK Penabur Gading Serpong",
      insignia: bee,
    },
    {
      code: "S035",
      names: ["Gabriella Anna Santoso, Kayla Theodora Wibisana"],
      school: "SMPK Kelapa Gading",
      insignia: bee,
    },
    {
      code: "S036",
      names: ["Fiorine Audiera Han"],
      school: "SMPK PENABUR Kota Modern",
      insignia: bee,
    },
  ];

	const winners = [
  ];
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
						<div in:fly={{ y: 50, duration: 500 }} class="bg-white rounded-lg shadow-lg p-4 z-10">
							<img
								class="h-[20rem] min-h-[20rem] w-[20rem] min-w-[20rem] object-contain"
								src={shown.insignia}
								alt="school logo"
							/>
						</div>
					{/key}

					<div class="flex flex-col">
						{#key shown}
							<div in:fly={{ delay: 100, y: 100, duration: 500 }}>
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
							<div in:fly={{ y: 35, duration: 500 }}>
								<div class="text-gray-700 text-4xl font-montserrat break-words">
									{shown.school}
								</div>
							</div>
						{/key}
					</div>
				</div>
				<div class="mt-8 w-full flex-grow max-w-2xl mx-auto p-4">
					<ul class="font-barlow-semi text-gray-700 text-xl space-y-1">
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
