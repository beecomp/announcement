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
  import witama from "./logo-witama.jpg";
  import xaverius from "./logo-xaverius.jpg";
	import bee from "./tightboi.png";
	
  const participants = [
    {
      code: "M001",
      names: ["Franklin Filbert"],
      school: "SMP Witama",
      insignia: witama,
    },
		{
			code: "M002",
			names: ["Adeline Fedora Cahyadi"],
			school: "SMP Xaverius 1 Bandarlampung",
			insignia: xaverius,
		},
		{
			code: "M003",
			names: ["Kenneth Lie", "Damian Ma"],
			school: "SMPK 6 PENABUR",
			insignia: penabur,
		},
		{
			code: "M004",
			names: ["Holly Natasha Sutantio", "Kathryne Ashley Sentosa"],
			school: "Mawar Sharon Christian School",
			insignia: mawar,
		},
    {
      code: "M005",
      names: ["Nathanael Richlie Kurniawan"],
      school: "SMPK PENABUR Gading Serpong",
      insignia: penabur,
    },
    {
      code: "M006",
      names: ["Jasper Rexx Putra Cakra", "Fakhri Musyaffa Ariyanto"],
      school: "Kharisma Bangsa",
      insignia: kharismabangsa,
    },
    {
      code: "M007",
      names: ["M. Rafi Qsan Baskoro", "Naufal Fadhlurrahman"],
      school: "SMP Kharisma Bangsa",
      insignia: kharismabangsa,
    },
    {
      code: "M009",
      names: ["Darren Tan", "Felipe Nathanael Corinthians Sitorus"],
      school: "SMP Kristen 2 Penabur",
      insignia: penabur,
    },
    {
      code: "M010",
      names: ["Valencia Hardjadinata", "Alexandrene Tanri"],
      school: "SMPK 7 PENABUR Jakarta",
      insignia: penabur,
    },
    {
      code: "M011",
      names: ["Karin Bunadi", "Daniel Timothy Taruna"],
      school: "SMPK 7 PENABUR JAKARTA",
      insignia: penabur,
    },
    {
      code: "M012",
      names: ["Ailin Liangga Putri", "Tristan Alexander Wong"],
      school: "SMP Cita Hati Christian School",
      insignia: bee,
    },
    {
      code: "M013",
      names: ["Imam Rasyid Rabbani", "Heydar Ali Akbar"],
      school: "SMPN 255 Jakarta",
      insignia: bee,
    },
    {
      code: "M014",
      names: ["Michael Cenreng", "Grace Lucretia"],
      school: "SMP Katolik Rajawali",
      insignia: rajawali,
    },
    {
      code: "M015",
      names: ["Ben Robinson", "Ethan Anderson"],
      school: "SMP PETRA 1",
      insignia: petra,
    },
    {
      code: "M016",
      names: ["Louis Wilson Gunawan", "Ethan Christopher Huang"],
      school: "SMPK 2 PENABUR",
      insignia: penabur,
    },
    {
      code: "M019",
      names: ["Najwa Lathiifah Saepudin", "Khairunnisa Athifah"],
      school: "SMP IT INSAN HARAPAN",
      insignia: it,
    },
    {
      code: "M022",
      names: ["Darren Joeve Tanujaya", "Elvin Rosadi"],
      school: "SMPK BPK PENABUR Bandar Lampung",
      insignia: penabur,
    },
    {
      code: "M023",
      names: ["Kevin Adi Senjaya"],
      school: "SMP Cahaya Bangsa Metro",
      insignia: cahayabangsa,
    },
    {
      code: "M024",
      names: ["Evan Syatia To", "Jason Jomono"],
      school: "SMPK 4 Penabur",
      insignia: penabur,
    },
    {
      code: "M025",
      names: ["Theo Manuel Santoso", "Gwen Tiffany Haryanto"],
      school: "SMP IPEKA Puri",
      insignia: ipeka,
    },
    {
      code: "M026",
      names: ["Metta Niyamacitta Exeliem"],
      school: "SMPK PENABUR KOTA MODERN",
      insignia: penabur,
    },
    {
      code: "M027",
      names: ["Luffy Lionheart Liduwan", "Willard Ricxie Phangara"],
      school: "SMPK 6 Penabur",
      insignia: penabur,
    },
    {
      code: "M028",
      names: ["Caroline Evangelina", "Helen Maurelle Wijayanti"],
      school: "SMPK Kolese Santo Yusup 2 Malang",
      insignia: kosayu,
    },
    {
      code: "M029",
      names: ["Clarissa Olivia Purwanto", "Kevin Kumala"],
      school: "SMPK Kolese Santo Yusup 2 Malang",
      insignia: kosayu,
    },
    {
      code: "M030",
      names: ["Neisha Calya Mahardhika", "Zidan Akrom Putra"],
      school: "SMP Pribadi Depok",
      insignia: kosayu,
    },
    {
      code: "M031",
      names: ["Leonardo Valerian", "Yvonnie Natasha"],
      school: "SMP Darma Yudha",
      insignia: darmayudha,
    },
    {
      code: "M032",
      names: ["Grace Christinalie", "Gilberto Lim"],
      school: "SMP DARMA YUDHA",
      insignia: darmayudha,
    },
    {
      code: "M033",
      names: ["Noell Raymon Putra Simamora", "Derrick Devs Chayrich"],
      school: "Darma Yudha",
      insignia: darmayudha,
    },
    {
      code: "M034",
      names: ["Neilson Huang", "Elia Siringoringo"],
      school: "SMP Darma Yudha",
      insignia: darmayudha,
    },
    {
      code: "M035",
      names: ["Gilbert Titus Calvin Marganti Hutapea"],
      school: "SMPN 92 JAKARTA",
      insignia: bee,
    },
    {
      code: "M038",
      names: ["Esther Gloria Abigail Mamesah", "Nadhif Aydin Adinandra"],
      school: "SMPN 2 Depok",
      insignia: bee,
    },
    {
      code: "M040",
      names: ["Ayra Kenanthi Putri S.", "Prita Salsabila"],
      school: "SMP Global Prestasi",
      insignia: globalprestasi,
    },
    {
      code: "M042",
      names: ["Rico Firmansyah", "Essenza Qurani Permata"],
      school: "SMP BUSTANUL MAKMUR GENTENG",
      insignia: bustanul,
    },
    {
      code: "M043",
      names: ["Firdasari Kusuma", "Mazaya Allessya Kusuma"],
      school: "SMPN 2 DEPOK",
      insignia: bee,
    },
    {
      code: "M044",
      names: ["Joshua Willson", "Cedric Kartawidjaja"],
      school: "SMPK Penabur Gading Serpong",
      insignia: penabur,
    },
    {
      code: "M046",
      names: ["Keiana Sethyaningrum", "Davin Sukandar"],
      school: "SMP Athalia",
      insignia: athalia,
    },
    {
      code: "M047",
      names: ["Kelsey Daveney Dicky", "Hanzel Clement Alpeso"],
      school: "SMP Athalia",
      insignia: athalia,
    },
    {
      code: "M048",
      names: ["Joleen Chelsea"],
      school: "Raffles School Kelapa Gading",
      insignia: raffles,
    },
    {
      code: "M049",
      names: ["Caroline Gracia Lendrian"],
      school: "Penabur International Kelapa Gading",
      insignia: penabur,
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
				<div class="mt-8 w-full flex-grow max-w-xl mx-auto p-2">
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
					class="block w-full mt-4 h-2 max-w-xl mx-auto bg-lavender rounded shadow p-4"
				/>
			</div>
		</div>
	</div>
</div>
