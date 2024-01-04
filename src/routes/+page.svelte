<script lang="ts">
	import { onMount } from 'svelte';
	import { blur, fade, fly, slide } from 'svelte/transition';
	import PortfolioElement from '../components/PortfolioElement.svelte';

	let lines: string[] = ['', ''];
	let showIcons = false;

	async function typeLine(lineIndex: number, line: string, delay: number, clearPreviousText: boolean = false): Promise<void> {
		if (clearPreviousText) {
			lines[lineIndex] = '';
		}

		for (let i = 0; i < line.length; i++) {
			lines[lineIndex] += line[i];
			await new Promise((resolve) => setTimeout(resolve, delay));
		}
	}

	async function eraseLine(lineIndex: number, delay: number): Promise<void> {
		for (let i = lines[lineIndex].length; i > 0; i--) {
			lines[lineIndex] = lines[lineIndex].slice(0, -1);
			await new Promise((resolve) => setTimeout(resolve, delay));
		}
	}

	async function delay(delay: number): Promise<void> {
		await new Promise((resolve) => setTimeout(resolve, delay));
	}

	onMount(async () => {
		const writeTime = 100;

		await delay(1000);

		await typeLine(0, 'Hey!', writeTime);

		await delay(700);

		await eraseLine(0, writeTime);

		await delay(500);

		await typeLine(0, "C'est Rayane,", writeTime, true);
		await typeLine(1, 'Votre développeur préféré', writeTime, true);

		await delay(500);

		showIcons = true;

		await delay(500);
	});
</script>

<header class="w-screen h-24 bg-[#18122B] relative">
	<img src="favicon.png" alt="Logo" class="w-16 h-16 absolute top-4 left-4" />

	<h1 class="text-xl md:text-4xl font-bold max-w-[50px] md:max-w-full text-white absolute left-24 top-1/2 -translate-y-1/2 right-12">Rayane Staszewski</h1>

	<nav class="absolute top-1/2 -translate-y-1/2 right-2 text-right md:text-left md:right-12 text-lg md:text-xl flex flex-col md:flex-row md:gap-x-8">
		<a href="#sites" class="text-white hover:underline">Mes sites</a>
		<a href="#logiciels" class="text-white hover:underline">Mes logiciels</a>
	</nav>
</header>

<section class="w-screen h-[400px] md:h-[700px] bg-[#252235] p-5 grid grid-cols-6 gap-y-20 md:gap-y-0 grid-rows-6 text-[#e4d9bc]">
	<p class="col-start-2 text-4xl md:text-7xl row-start-2 font-bold col-span-3">{lines[0]}</p>
	<p class="col-start-2 text-xl md:text-4xl row-start-3 font-bold col-span-3">{lines[1]}</p>

	{#if showIcons}
		<div transition:blur={{ duration: 1000 }} class="col-start-1 md:col-start-3 text-4xl md:row-start-5 row-span-2 font-bold col-span-6 md:col-span-2 grid grid-cols-6 grid-rows-2 md:grid-rows-3 gap-y-2 md:gap-y-5">
			<img src="icons/csharp.svg" alt="C#" class="w-full h-full" />
			<img src="icons/typescript-icon.svg" alt="TypeScript" class="w-full h-full" />
			<img src="icons/html-5.svg" alt="HTML5" class="w-full h-full" />
			<img src="icons/tailwindcss-icon.svg" alt="Tailwind CSS" class="w-full h-full" />
			<img src="icons/react.svg" alt="React" class="w-full h-full" />
			<img src="icons/svelte-icon.svg" alt="Svelte" class="w-full h-full" />
			<img src="icons/python.svg" alt="Python" class="w-full h-full" />
			<img src="icons/nodejs-icon.svg" alt="NodeJS" class="w-full h-full" />
			<img src="icons/sqlite-icon.svg" alt="SQLite" class="w-full h-full" />

			<img src="icons/git-icon.svg" alt="Git" class="w-full h-full" />
			<img src="icons/visual-studio-code.svg" alt="Visual Studio Code" class="w-full h-full" />
			<img src="icons/visual-studio.svg" alt="Visual Studio" class="w-full h-full" />
		</div>

		<!-- <img src="moi.webp" alt="Moi" class="col-start-5 row-start-2 row-span-4 col-span-2 object-contain w-full h-full" transition:fade={{ duration: 1000 }} /> -->
	{/if}
</section>

<section class="w-screen flex justify-center text-white mt-14">
	<div class="w-[90%] md:w-[70%]">
		<h1 class="text-3xl md:text-5xl font-bold" id="sites">Certains de mes sites internet</h1>

		<br />

		<PortfolioElement
			title="Random Github Repo"
			description="Si vous cherchez de l'inspiration pour vos projets futurs, explorez ce site unique qui vous présentera une variété de projets de développeurs du monde entier de manière aléatoire."
			image="assets/rgr.png"
			link="https://www.randomgithubrepo.site/"
		/>

		<br />

		<PortfolioElement
			title="SignaMath - Dresseur de tableau de signes et de variations"
			description="Dresser le tableau de signes, de variations ou de convexité d'une fonction mathématique n'a jamais été aussi simple grâce à cet outil mathématique en ligne."
			image="assets/signamath.png"
			link="https://www.signamath.online/"
		/>

		<br />

		<PortfolioElement
			title="Quran Caption"
			description="Cette application web de montage vidéo vous permet de créer des sous-titres pour vos vidéos de récitation du Coran et de les incruster directement sur la vidéo."
			image="assets/qurancaption.png"
			link="https://www.qurancaption.com/"
		/>

		<br />

		<PortfolioElement
			title="Turing Machine Box"
			description="Cette machine en ligne vous permet de créer et de simuler des algorithmes de machine de Turing ainsi que de les visualiser en temps réel."
			image="assets/turingmachinebox.png"
			link="https://turing-machine-box.vercel.app/"
		/>

		<br />

		<PortfolioElement
			title="Turing Machine Box"
			description="Cette machine en ligne vous permet de créer et de simuler des algorithmes de machine de Turing ainsi que de les visualiser en temps réel."
			image="assets/turingmachinebox.png"
			link="https://turing-machine-box.vercel.app/"
		/>

		<br />
		<br />
		<br />

		<h1 class="text-3xl md:text-5xl font-bold" id="logiciels">Certains de mes logiciels</h1>

		<br />

		<PortfolioElement
			title="Cheap Flight Notifier"
			description="Réservez vos vols au meilleur prix grâce à ce logiciel qui vous permet de recevoir des notifications sur votre téléphone lorsque les tarifs de vos vols Tui Fly, RyanAir ou EasyJet évoluent."
			image="assets/cfn.png"
			link="https://github.com/zonetecde/Cheap-Flight-Notifier"
		/>
		<br />

		<PortfolioElement
			title="WPF Infinite Canvas (& Game of Life)"
			description="Ce contrôle WPF permet de créer un quadrillage infini dans lequel vous pouvez vous déplacer et déposer d'autres éléments amovibles."
			image="assets/wic.gif"
			link="https://github.com/zonetecde/Wpf-Infinite-Canvas"
		/>
		<br />

		<PortfolioElement title="Maze Generator" description="Visualisez la génération de labyrinthes selon l'algorithme de Wilson." image="assets/mazegenerator.png" link="https://github.com/zonetecde/Maze-Generator" />
		<br />

		<PortfolioElement
			title="Gestionnaire de tâche"
			description="Gérez vos projets personnels en suivant vos futures tâches à accomplir et en organisant votre travail."
			image="assets/gdt.png"
			link="https://github.com/zonetecde/Gestionnaire-de-tache"
		/>
		<br />

		<PortfolioElement title="House of Quran" description="Écoutez, lisez et mémorisez le Coran sans connexion internet avec plus de 40 récitants différents." image="assets/hoq.png" link="https://github.com/zonetecde/House-of-Quran" />
		<br />

		<PortfolioElement
			title="Who's the funniest ?"
			description="Affrontez-vous avec vos amis pour créer le rire le plus contagieux. Un vote est organisé pour qualifier le vainqueur !"
			image="assets/wtf.png"
			link="https://github.com/zonetecde/Who-s-the-funniest"
		/>
		<br />

		<PortfolioElement title="Chess Zone" description="Un jeu d'échecs multijoueur connecté en ligne." image="assets/chess.png" link="https://github.com/zonetecde/Chess-Zone" />

		<br />

		<PortfolioElement title="Type Spone" description="Entraînez-vous à écrire au clavier tout en vous amusant avec ce jeu éducatif." image="assets/typespone.jpg" link="https://github.com/zonetecde/Type-Spone" />

		<br />

		<PortfolioElement title="2048" description="Le célèbre jeu 2048" image="assets/2048.png" link="https://github.com/zonetecde/2048" />

		<br />

		<PortfolioElement title="ESCII" description="Crypter des messages secrets dans vos images" image="assets/escii.png" link="https://github.com/zonetecde/ESCII" />
		<br />

		<PortfolioElement title="Scrabble" description="Jouez au jeu du scrabble en ligne" image="assets/scrabble.png" link="https://github.com/zonetecde/Scrabble" />

		<br />

		<p><i>Et une dizaine d'autres...</i></p>

		<br />
		<br />
	</div>
</section>
