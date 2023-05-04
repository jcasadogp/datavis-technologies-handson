<script>
  import { json } from "d3-fetch";
  import { onMount } from "svelte";

  import Controls from "./Controls.svelte";
  import Scatterplot from "./Scatterplot.svelte";

  export let index_exercise = 0;
  
  // Load the data
  let data = null;
  // let data_year = null;
  onMount(async () => {
    data = await json("/data/gapminder.json");
    console.log(data)

    // data_year = data[index_exercise]
    // console.log(data_year)
  });
</script>

{#if !data}
  <p>Loading the data, please wait...</p>
{:else}
  <div>
    <Scatterplot data={data[index_exercise]['countries']} />
    <Controls bind:index_control={index_exercise} />
  </div>
{/if}
