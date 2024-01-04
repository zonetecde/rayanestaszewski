<script lang="ts">
	export let title: string;
	export let description: string;
	export let image: string;
	export let link: string;
</script>

<div class="grid md:grid-cols-6 grid-rows-2 grid-cols-1 md:grid-rows-1 md:gap-x-5 gap-y-5">
	<a href={link} target="_blank" rel="noopener noreferrer" class="md:col-start-1 row-start-1 md:col-span-4 md:row-span-2 flex justify-center items-center bg-[#e4d9bc] rounded-xl shadow-xl">
		<img src={image} alt={title} class="w-full h-full rounded-xl object-cover" />
	</a>

	<div class="md:col-start-5 row-start-2 md:row-start-1 col-span-2 row-span-2 flex flex-col gap-y-5">
		<a href={link} target="_blank" class="text-2xl font-bold hover:underline underline-offset-4">{title}</a>
		<p class="text-lg text-justify">{description}</p>

		<a href={link} target="_blank" class="text-center mt-auto w-full px-12 py-2 rounded-lg border-2 border-[#473d4d] text-black hover:scale-105 duration-150 shadow-xl bg-[#796983]">Visiter</a>
	</div>
</div>
