<script>
  // A datapoint looks like this:
  // {continent:"europe"
  // country:"Yugoslavia"
  // income:null
  // life_exp:null
  // population:4687422}

  import { scaleBand, scaleLinear } from 'd3-scale';
  import { min, max, extent} from "d3-array";

  // Dimensions
  const [height, width] = [400, 600];
  const margin = { top: 50, right: 5, bottom: 55, left: 50 };
  const innerWidth = width - margin.left - margin.right;
  const innerHeight = height - margin.top - margin.bottom;

  // Data
  export let datapoints = []; //Because of the export we can access this variable from outside. 
  console.log('=======================================')
  console.log('(2) Scatterplot script')
  console.log('(2)', datapoints)

  // Scales
  // const xScale = scaleLinear().domain([0, max(datapoints, d => d.income)]).range([0, innerWidth]);
  // const yScale = scaleLinear().domain([0, max(datapoints, d => d.life_exp)]).range([innerHeight, 0]);
</script>

<svg viewBox="0 0 {width} {height}" style="max-width: {width}px">
  <g transform="translate({margin.left}, {margin.top})">
    <!-- <circle cx={xScale(763)} cy={yScale(36.6)} r=10></circle> -->
    <!-- {#each datapoints as datapoint,i}
        <circle cx={+datapoint.income} cy={+datapoint.life_exp} r=10></circle>
    {/each} -->
  </g>
</svg>
