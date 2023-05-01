<script>
    import * as d3 from "d3"
    // Dimensions
    const width = 600;
    const height = 300;
    const margin = { top: 10, right: 10, bottom: 30, left: 60 };
    const innerWidth = width - margin.left - margin.right;
    const innerHeight = height - margin.top - margin.bottom;
  
    // Array
    const data = [
      { service: "Netflix", viewers: 2.9 },
      { service: "Amazon Prime Video", viewers: 1.3 },
      { service: "Disney+", viewers: 2.1 },
      { service: "Hulu", viewers: 0.9 },
      { service: "Apple TV", viewers: 1.1 },
      { service: "Rakuten", viewers: 0.4 }
    ];

    let services = [];
    for(const d of data){
      services.push(d.service);
    }

    const viewers_range = d3.extent(data,(d)=>d.viewers);
    let scaler_y = d3.scaleLinear().domain([0, 3]).range([innerHeight,0]);
    let scale_xbar = d3.scaleBand().domain(services).range([0,innerWidth]);

    const xaxis = d3.axisBottom(scale_xbar);
    const yaxis = d3.axisLeft(scaler_y);

    function addleftaxis(){d3.select('#leftaxis').call(yaxis);}
    function addbottomaxis(){d3.select('#bottomaxis').call(xaxis);}


  </script>
  
  <!-- setting a viewBox and max-width allows the SVG to shrink but not grow! -->
  <svg viewbox="0 0 {width} {height}" style="max-width: {width}px">
    <text x="-50" y=130 transform="rotate(-90 0 115)">viewers</text>
    <g id="leftaxis" use:addleftaxis transform={`translate(${margin.left-20},${margin.top})`}> </g>
    <g transform={`translate(${margin.left},${margin.top})`}>
      <!--  -->
      {#each data as p}
      <rect x={scale_xbar(p.service)} y={innerHeight-scaler_y(p.viewers)} height={scaler_y(p.viewers)} width=50 fill="skyblue"> </rect>
      {/each}
    </g>
    <g id="bottomaxis" use:addbottomaxis transform={`translate(${40}, ${height-margin.bottom})`}></g>
  </svg>



  