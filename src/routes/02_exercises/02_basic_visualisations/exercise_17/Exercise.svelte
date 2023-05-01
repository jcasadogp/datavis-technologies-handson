<script>
  import { scaleLog } from 'd3-scale';
  import { min, max, extent} from "d3-array";

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
  </script>

<style>
  circle {
      fill: steelblue;
  }
</style>

<svg viewBox="0 0 {width} {height}">
  <g transform="translate({margin.left},{margin.top})">
    <g transform="translate(0,{innerHeight / 2})">
      {#each values as value}
      <circle cx={scale(value)} 
              cy=0
              r=10 />
    {/each}
  </g>
  </g>
</svg>