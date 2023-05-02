<script>
    import { onMount } from 'svelte';
    import Scatterplot from './Scatterplot.svelte';

    let data = null;
    onMount(async () => {
        const res = await fetch('/data/gapminder.json')
        let data_tmp = await res.json()
        
        data = data_tmp.find(datapoint => datapoint.year === '1800')['countries'];
    });
    
</script>

{#if data == null}
    <p>The data is being loaded...</p>
{:else}
    <Scatterplot datapoints={data} />     
{/if}