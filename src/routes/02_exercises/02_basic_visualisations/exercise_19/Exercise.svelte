<script>
    import * as d3 from "d3";
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
    const scalex = d3.scaleLinear().domain([0,10]).range([0,innerWidth]);
    const scaley = d3.scaleLinear().domain([0,4]).range([0,innerHeight]);
    const classcolor = d3.extent(values,(d)=>d.category);
    const scalecolor = d3.scaleOrdinal().domain(classcolor).range(d3.schemeDark2);

  </script>
  
  
  <svg viewBox="0 0 {width} {height}">
    <g transform="translate({margin.left},{margin.top})">
      <!--  -->
      {#each values as value}
      <circle
      cx={scalex(value.x)}
      cy={scaley(value.y)}
      r="7"
      style="fill:{scalecolor(value.category)}"
      ></circle>

      <text
      x={scalex(value.x)}
      y={scaley(value.y)-10}>
        {value.y}
      </text>

      <line
      x1={scalex(value.x)}
      x2={scalex(value.x)}
      y1={scaley(value.y)}
      y2={height}
      stroke="black">
      </line>

      {/each}
    </g>
  </svg>
  <style>
    text {
      text-anchor: middle;
      font-size: small;
    }
  </style>
  