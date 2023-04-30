
<script>
    import{scaleLog} from 'd3-scale';
    import {axisBottom} from "d3-axis";
    import {select} from "d3-selection";
    // Dimensions
    const width = 800;
    const height = 100;
    const margin = { top: 5, right: 5, bottom: 25, left: 5 };
    const innerWidth = width - margin.left - margin.right;
    const innerHeight = height - margin.top - margin.bottom;

    const logscaler = scaleLog()
                      .domain([1,10])
                      .range([1,innerWidth]);
    let axisbottom = axisBottom(logscaler);
    function func1(x){axisbottom(select(x))};
    // Array
    const values = [2, 4, 6, 7, 9];
  </script>


  <svg viewBox="0 0 {width} {height}">
    <g transform="translate({margin.left},{margin.top})">
      <!--  -->
      {#each values as value}
      <circle fill="navy" cx={logscaler(value)-5} cy={innerHeight/2} r="10" />
      {/each}
    </g>
    <g transform ="translate(0,70)" use:func1={'g'}></g>
    <text font-size="15" x=380 y=95>x-lable</text>
  </svg>
  
  