<script lang="ts">
	import { onMount } from 'svelte';
	import { blur, fade, fly, slide } from 'svelte/transition';

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
		await typeLine(1, 'Votre développeur full-stack', writeTime, true);

		await delay(500);

		showIcons = true;

		await delay(500);
	});
</script>

<header class="w-screen h-24 bg-[#18122B]"></header>

<section class="w-screen h-[60%] bg-[#252235] p-5 grid grid-cols-6 grid-rows-6 text-[#e4d9bc]">
	<p class="col-start-2 text-7xl row-start-2 font-bold col-span-3">{lines[0]}</p>
	<p class="col-start-2 text-4xl row-start-3 font-bold col-span-3">{lines[1]}</p>

	{#if showIcons}
		<div transition:blur={{ duration: 1000 }} class="col-start-3 text-4xl row-start-5 row-span-2 font-bold col-span-2 grid grid-cols-6 grid-rows-3 gap-y-5">
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
	{/if}
</section>
