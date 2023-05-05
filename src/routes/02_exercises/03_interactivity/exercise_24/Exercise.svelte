<script>
  import { json } from "d3-fetch";
  import { onMount } from "svelte";

  import Controls from "./Controls.svelte";
  import Scatterplot from "./Scatterplot.svelte";

  export let index_exercise = 0;
  export let selected_continents_exercise = ["europe", "asia", "americas", "africa"];
  
  // Load the data
  let data = null;
  // let data_year = null;
  onMount(async () => {
    data = await json("/data/gapminder.json");
    console.log(data)

    console.log()
  });
</script>

{#if !data}
  <p>Loading the data, please wait...</p>
{:else}
  <div>
    <Scatterplot data={data[index_exercise]['countries'].filter(d => selected_continents_exercise.includes(d.continent))} />
    <Controls bind:index_control={index_exercise} bind:selected_continents={selected_continents_exercise}/>
  </div>
{/if}
