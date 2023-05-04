<script>
  import Exercise from "./Exercise.svelte";

  // Properties
  // export let data = []; // Here the data is only for knowing which continents and years exist
  const continents = ["europe", "asia", "americas", "africa"];

  export let index_control = 0;
  let playing = false;
  let countYear;

  function playPause(){
    if (playing == true){
      clearInterval(countYear)
    }else{
      countYear = setInterval(increaseYear, 100);
    }
    playing = !playing
  }

  function increaseYear(){
    index_control += 1
    if (index_control > 214){
      resetYear()
    }
  }

  function resetYear(){
    index_control = 0;
  }

</script>


<div class="controls-group">
  <button on:click={playPause}>Play Pause</button>
  <button on:click={resetYear}>Reset</button>
  <div>
    <input type="range" min="0" max="214" bind:value={index_control}> {index_control + 1800}
  </div>
  <div>
    <!-- <select value={selected} on:change="{() => answer = ''}">
      {#each continents as continent}
        <option value={continent}>
          {continent}
        </option>
      {/each}
    </select> -->
  </div>
</div>


<style>
  .controls-group {
    text-align: center;
  }
  .controls-group button {
    background-color: #04AA6D;
    border: 1px solid green; /* Green border */
    color: white; /* White text */
    margin: 10px;
    padding: 10px 24px;
  }
</style>
