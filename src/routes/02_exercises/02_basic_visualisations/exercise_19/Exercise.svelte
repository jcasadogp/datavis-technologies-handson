<script>
    import { scaleLinear, scaleOrdinal } from 'd3-scale';
    import { min, max, extent} from "d3-array";
    import { schemeDark2 } from 'd3-scale-chromatic'
    
    // Dimensions
    const width = 800;
    const height = 100;
    const margin = { top: 20, right: 5, bottom: 5, left: 5 };
    const innerWidth = width - margin.left - margin.right;
    const innerHeight = height - margin.top - margin.bottom;
  
    // Array
    const values = [
      { x: 2, y: 1, category: "cat1" },
      { x: 4, y: 2, category: "cat3" },
      { x: 6, y: 1, category: "cat2" },
      { x: 7, y: 3, category: "cat3" },
      { x: 9, y: 1, category: "cat2" }
    ];

    const unique_categories = [...new Set(values.map(v => v.category))]

    // Scales
    const xScale = scaleLinear().domain([min(values, v => v.x), max(values, v => v.x)]).range([0, innerWidth])
    const yScale = scaleLinear().domain([min(values, v => v.y), max(values, v => v.y)]).range([0, innerHeight])
    const catScale = scaleOrdinal(schemeDark2).domain(unique_categories)

  </script>
  
  <svg viewBox="0 0 {width} {height}">
    <g transform="translate({margin.left},{margin.top})">
      {#each values as value}
        <circle cx={xScale(value.x)} 
                cy={yScale(value.y)} 
                r=10
                style={"fill:" + catScale(value.category)}
                class:valueLabel={value.category}
                >
              </circle>
        <line x1={xScale(value.x)} y1={yScale(value.y)} x2={xScale(value.x)} y2={innerHeight}></line>
        <text x={xScale(value.x)} y={yScale(value.y)-10}>{value.category}</text>
      {/each}
    </g>
  </svg>
  
  <style>
    text {
      text-anchor: middle;
      font-size: small;
    }
    line {
      stroke: black
    }
  </style>
  