<script>
    import { scaleBand, scaleLinear } from 'd3-scale';
    import { min, max, extent} from "d3-array";
    import { axisLeft, axisBottom } from 'd3-axis';
    import { select } from 'd3-selection';
    
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

    const barWidth = (innerWidth / data.length) -10;

    // Scales
    const xScale = scaleBand().domain(data.map((d) => d.service)).range([0, innerWidth]);
    const yScale = scaleLinear().domain([0, max(data, d => d.viewers)]).range([innerHeight, 0]);

    function leftAxisBuilder(handle){
      let axisGen = axisLeft(yScale)
      let yAxis = axisGen(select(handle))
    }

    function bottomAxisBuilder(handle){
      let axisGen = axisBottom(xScale)
      let xAxis = axisGen(select(handle))
    }

  </script>
  
  <svg viewbox="0 0 {width} {height}" style="max-width: {width}px">
    <g transform={`translate(${margin.left},${margin.top})`}>
      {#each data as d}
        <rect x={xScale(d.service)} y={yScale(d.viewers)} width={barWidth} height={innerHeight - yScale(d.viewers)} fill="blue"></rect>
      {/each}
      <g use:leftAxisBuilder></g>
      <g transform={`translate(0,${innerHeight})`} use:bottomAxisBuilder></g>
    </g>
  </svg>

  <style>
    rect{
      fill:steelblue;
      opacity: 0.8;
    }
    rect:hover{
      fill:red;
    }
  </style>