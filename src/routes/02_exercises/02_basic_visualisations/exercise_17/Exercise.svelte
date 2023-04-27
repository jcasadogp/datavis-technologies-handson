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
      fill-opacity: 0.5;
  }
</style>

<svg viewBox="0 0 {width} {height}">
  <g transform="translate({margin.left},{margin.top})">
    {#each values as value}
      <circle cx={scale(value)} 
              cy=10 
              r=10 />
    {/each}
  </g>
</svg>