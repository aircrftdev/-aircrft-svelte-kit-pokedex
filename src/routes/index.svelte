<script>
import PokemanCard from "../components/pokemanCard.svelte";
import {pokemon, fetchPokemon} from "../pokestore";

let searchTerm = "";
let filteredPokemon = [];

$: {
    if(searchTerm){
        filteredPokemon = $pokemon.filter( pokeman => pokeman.name.toLowerCase().includes(searchTerm.toLowerCase()));
    }
    else {
        filteredPokemon = [...$pokemon];
    }
}

fetchPokemon();
</script>
<svelte:head>
	<title>Aircrft Problem / Solution Stack</title>
</svelte:head>

<h1 class="text-4xl text-center my-8 uppercase">Aircrft Problem / Solution Stack</h1>
<p>Welcome the Aircrft powered Problem / Solution Stack - the world's most up-to-the minute realtime open source problem and solution database. "Craigslist for problem solving!" Our moonshot mission is to "Solve the problem of problem-solving". The Aircrft Problem/Solution matching algorithm matches people to the problem(s) they are deeply passionate about solving. Thiers no wrong work, just the wrong person doing the wrong work.</p>
<br>
<p>The world’s most precious resource is the passionate and committed human mind.</p>
<br>
<p>Organized in 4 core problem stacks: Urgent, Future, Common, and Anything Else.</p>
<input class="w-full rounded-md text-lg p-4 border-2 border-gray-200" bind:value={searchTerm} placeholder="Search Pokemon">
<div class="py-4 grid gap-4 md:grid-cols-2 grid-cols-1">
    
    {#each filteredPokemon as pokeman}
            <PokemanCard pokeman={pokeman}/>
    {/each}
</div>
<style>
    h1 {
        color: rgb(44, 37, 148);
    }
</style> 
