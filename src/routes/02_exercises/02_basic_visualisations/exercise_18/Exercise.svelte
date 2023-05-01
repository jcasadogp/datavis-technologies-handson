<script>
  
  import { scaleLog } from 'd3-scale';
  import { min, max, extent} from "d3-array";
  import { axisBottom } from 'd3-axis';
  import { select } from 'd3-selection';

  // Dimensions
  const width = 800;
  const height = 100;
  const margin = { top: 5, right: 5, bottom: 5, left: 5 };
  const innerWidth = width - margin.left - margin.right;
  const innerHeight = height - margin.top - margin.bottom;

  // Array
  const values = [2, 4, 6, 7, 9];

  // Scale
  const scale = scaleLog().base(10).domain([1, max(values)]).range([0, innerWidth]);

  function axisBuilder(handle){
    let axisGen = axisBottom(scale)
    let xAxis = axisGen(select(handle))
  }

  </script>

<svg viewBox="0 0 {width} {height}">
  <g transform="translate({margin.left},{margin.top})">
    <g transform="translate(0,{innerHeight / 2})" use:axisBuilder>
      {#each values as value}
      <circle cx={scale(value)} cy=0 r=10 />
    {/each}
  </g>
  </g>
</svg>

<style>
  circle {
      fill: steelblue;
  }
  circle:hover{
    fill: red;
    fill-opacity: 1;
  }
</style>


