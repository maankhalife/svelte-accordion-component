<script>

	import { continents } from './continentsData.js';
	import Accordion from '@maan.khalife/accordion@1.0.1';

	let active = "-1"; //Identifies which index is active
	
	//False: Opens one item at a time, 
	// True: Opens/Closes any item with possibility of opening multipe items
	let keepActive = false;  
	
</script>

<svelte:head>
	<link href="https://unpkg.com/tailwindcss@^2/dist/tailwind.min.css" rel="stylesheet" />
</svelte:head>

<div 
class="
    border-gray-200 
    border-4
    rounded-sm
">
	
	<div class="space-y-4">
		<button on:click={() => keepActive = !keepActive}
			class="px-4 py-2 w-full block bg-blue-400 text-white">
				Click to keep single/multiple item(s) open
			</button>
		
		{#each continents as {id, name, population, desc}}

			{#if keepActive}	
				<Accordion 	id="{id}" 
										title="{name}" 
										subTitle="{population}" 
										content="{desc}" 
										/>
			{/if}

			{#if !keepActive}
				<Accordion bind:active 	id="{id}" 
										title="{name}" 
										subTitle="{population}" 
										content="{desc}" 
										/>
			{/if}

		{/each}
		
	</div>
</div>