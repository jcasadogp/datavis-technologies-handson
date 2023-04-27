<script>
    import { scaleBand, scaleLinear } from 'd3-scale';
    import { min, max, extent} from "d3-array";
    
    // Dimensions
    const width = 600;
    const height = 300;
    const margin = { top: 10, right: 10, bottom: 30, left: 60 };
    const innerWidth = width - margin.left - margin.right;
    const innerHeight = height - margin.top - margin.bottom;

    
    // xTicks = data.map((d) => d.service);
    // const barWidth = innerWidth / xTicks.length;
  
    // Array
    const data = [
      { service: "Netflix", viewers: 2.9 },
      { service: "Amazon Prime Video", viewers: 1.3 },
      { service: "Disney+", viewers: 2.1 },
      { service: "Hulu", viewers: 0.9 },
      { service: "Apple TV", viewers: 1.1 },
      { service: "Rakuten", viewers: 0.4 }
    ];

    // Scales
    const xScale = scaleBand().domain(data.map((d) => d.service)).range([0, innerWidth]);
    //.range([margin.left, width - margin.right]);
    const yScale = scaleLinear().domain([0, max(data, d => d.viewers)]).range([0, innerHeight]);
    //.range([height - margin.bottom, margin.top]);

  </script>
  
  <svg viewbox="0 0 {width} {height}" style="max-width: {width}px">
    <g transform={`translate(${margin.left},${margin.top})`}>
      {#each data as d, i}
      <rect x={xScale(d.service)} y={innerHeight} width=40 height="{yScale(d.viewers)}"fill="red"/>
      <rect x={xScale(d.service)} y={0} width=60 height="{yScale(d.viewers)}"fill="green"/>
      <text x={xScale(d.service)} y={yScale(d.viewers)+10}>{d.service}</text>
      {/each}
    </g>
  </svg>

  <style>
    text {
      text-anchor: middle;
      font-size: large;
    }
  </style>