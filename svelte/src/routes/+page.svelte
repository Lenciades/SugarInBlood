<script>
import { base } from '$app/paths';

//--- base data from the .js sibling ---
export let data

//--- Components ---
import FoodsTable from '../lib/FoodsTable.svelte';
import FilterByInitial from '../lib/FilterByInitial.svelte';

import FoodsList from '../lib/FoodsList.svelte';
import TotalMacros from '../lib/TotalMacros.svelte';


//--- State Variables ---

let foods = data.foods
$: favoriteFoods = []
$: selectedFoods = []
$: totalMeals = []
$: totalMacros = {}

</script>

<div class ='container flex flex-wrap'>
    <div class= 'max-w-lg'>
        <!--<FilterByInitial rows = {foods} bind:filteredRows = {foodsToShow}/>-->
        
        {#if foods}
        <FoodsTable rows = {foods} bind:selectedRows = {selectedFoods} bind:favorites = {favoriteFoods}/>
        {/if}
    </div>
    <div class='max-w-lg'>
        {#if selectedFoods.length}
            {#if selectedFoods.length}
            <FoodsList bind:listedFoods = {selectedFoods} bind:total = {totalMeals}/>
            {/if}
            {#if totalMeals.length !== 0}
            <TotalMacros bind:meals = {totalMeals} bind:totalMacros = {totalMacros}/>
            {/if}
        {/if}
    </div>
</div>

<style>

/*
colors:{
    'carb-dark': '#865439',
    'carb-light': '#c68b59',
    'fat-dark': '#face7f',
    'fat-light': '#fcf0c8',
    'kcal-dark': '#32502e',
    'kcal-light': '#406343',
    'protein-dark': '#630a10',
    'protein-light' : '#911f27',
}
*/

</style>
