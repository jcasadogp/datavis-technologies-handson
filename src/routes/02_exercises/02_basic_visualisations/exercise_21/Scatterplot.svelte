<script>
  // A datapoint looks like this:
  // {continent:"europe"
  // country:"Yugoslavia"
  // income:null
  // life_exp:null
  // population:4687422}

  import { scaleBand, scaleLinear } from 'd3-scale';
  import { min, max, extent} from "d3-array";
  import { axisLeft, axisBottom } from 'd3-axis';
  import { select } from 'd3-selection';

  // Dimensions
  const [height, width] = [400, 600];
  const margin = { top: 50, right: 5, bottom: 55, left: 50 };
  const innerWidth = width - margin.left - margin.right;
  const innerHeight = height - margin.top - margin.bottom;

  // Data
  export let datapoints = []; //Because of the export we can access this variable from outside. 

  // Scales
  const xScale = scaleLinear().domain([0, max(datapoints, d => d.income)]).range([0, innerWidth]);
  const yScale = scaleLinear().domain([0, max(datapoints, d => d.life_exp)]).range([innerHeight, 0]);

  // Axis
  function leftAxisBuilder(handle){
    let axisGen = axisLeft(yScale)
    let yAxis = axisGen(select(handle))
  }

  function bottomAxisBuilder(handle){
    let axisGen = axisBottom(xScale)
    let xAxis = axisGen(select(handle))
  }
</script>

<svg viewBox="0 0 {width} {height}" style="max-width: {width}px">
  <g transform="translate({margin.left}, {margin.top})">
    <rect></rect>
    {#each datapoints as datapoint,i}
        <circle cx={xScale(+datapoint.income)} cy={yScale(+datapoint.life_exp)} r=5></circle>
    {/each}
    <g use:leftAxisBuilder></g>
    <g transform={`translate(0,${innerHeight})`} use:bottomAxisBuilder></g>
    <text transform="translate({innerWidth / 2}, {innerHeight+35})" >Income</text>
  </g>
</svg>

<style>
  circle{
    fill: steelblue;
    opacity: 0.8;
  }
  text{
    text-anchor: middle;
  }
</style>
