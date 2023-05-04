<script>
    // Dimensions
    const width = 800;
    const height = 100;
    const margin = { top: 10, right: 20, bottom: 20, left: 20 };
    const innerWidth = width - margin.left - margin.right;
    const innerHeight = height - margin.top - margin.bottom;
  
    // Arrays
    const points = [
      innerWidth / 2 - 150,
      innerWidth / 2 - 75,
      innerWidth / 2,
      innerWidth / 2 + 75,
      innerWidth / 2 + 150
    ];

    // Color variable
    let color = 'darkred';

    function cssVariables(node, variables) {
      setCssVariables(node, variables);
      
      return {
        update(variables) {
          setCssVariables(node, variables);
        }
      }
    }
    function setCssVariables(node, variables) {
      for (const name in variables) {
        node.style.setProperty(`--${name}`, variables[name]);
      }
    }
  
    // All lights with a higher index are on!
    let index = points.length;
    function countDown(){
      index -= 1;

      if(index == -1){
        color = 'darkgreen';
        clearInterval()
      }
    }

    setInterval(countDown, 1000);
  </script>
  
  <svg viewBox="0 0 {width} {height}" use:cssVariables={{color}}>
    <g transform="translate({margin.left},{margin.top})">
      {#each points as point,i}
          <circle cx={point} cy={innerHeight / 2} r=30
          class:turn_on="{point && i >= index}"
          ></circle>
          
      {/each}
    </g>
  </svg>

  <style>
    circle {
      fill: var(--color);
      fill-opacity: 0.3;
    }
    circle.turn_on {
      fill: var(--color);
      fill-opacity: 1;
    }
  </style>
  