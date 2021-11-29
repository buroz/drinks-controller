<script lang="ts">
	import Alcohol from './components/Alcohol.svelte';

	let drinks: Array<{
		img: string,
		key: string,
	}> = [];

	for (const key in localStorage){
		const item = localStorage.getItem(key);

		if (item) {
			drinks = drinks.concat({
				img: `${key}.png`,
				key,
			});
		}
	}

	const addAlcohol = () => {
		drinks = drinks.concat({
			img: 'https://www.thecocktaildb.com/images/media/drink/vqwpsp1472668169.jpg',
			key: 'beer'
		})
	}
</script>

<main class="container mx-auto">
	<!-- <input class="w-full boreder-1 rounded p-2 text-2xl" />
	
	<button class="bg-green-600 rounded text-white font-bold py-2 px-3 w-full my-3" on:click={addAlcohol}>Add Alcohol</button> -->

	{#each drinks as { img, key }}
		<Alcohol img={img} key={key} />
	{/each}

</main>

<style>
</style>
