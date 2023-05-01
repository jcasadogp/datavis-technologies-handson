<script>
    import { onMount } from 'svelte';
    import Scatterplot from './Scatterplot.svelte';

    console.log('=======================================')
    console.log('(1) Exercise script')
    
    let data = null;
    onMount(async () => {
        console.log("(1) The data is being loaded...");
        const res = await fetch('http://localhost:5173/data/gapminder.json')
        let data_tmp = await res.json()
        
        var data = await data_tmp.find(datapoint => datapoint.year === '1800')['countries'];
        console.log('(1)', data)
        console.log("(1) Data loaded!");
    });
    console.log('(1) Script finished!')
</script>

{#await data}
    <p>The data is being loaded...</p>
{:then data}
    <Scatterplot datapoints={data} /> 
{/await}