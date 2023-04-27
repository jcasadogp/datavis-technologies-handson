<script>
  const width = 400;
  const height = 400;
  const margin = { top: 5, right: 5, bottom: 5, left: 5 };
  const innerWidth = width - margin.left - margin.right; //80
  const innerHeight = height - margin.top - margin.bottom; //80
</script>

<svg viewBox="0 0 {width} {height}">
  <g transform="translate({margin.left}, {margin.top})">
    <!-- <rect x=0 y=0 width={innerWidth} height={innerHeight} /> -->
    <circle cx={innerWidth / 2} cy={innerHeight / 2} r="20" fill="teal" />
  </g>
</svg>

<style>
  svg {
    border: 1px solid black;
    border-radius: 5px;
  }
</style>