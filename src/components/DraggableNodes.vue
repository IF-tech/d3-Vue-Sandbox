<template>
    <div>
        <svg width="960" height="600"></svg>
    </div>
</template>

<script>
import * as d3 from "d3"
export default {
    name: 'SandboxDraggablenodes',

    data() {
        return {
            
        };
    },

    mounted() {
    const width = 960;
    const height = 600;
    const svg = d3 // use d3 to create the svg or scaleable vector graphics box to draw the chart on
    .select("svg") // select the svg
    .attr("height", height) // make the svg as tall as the height variable
    .attr("width", width);
 
  

let graph = {
    nodes: [
      { name: "Alice" },
      { name: "Bob" },
      { name: "Chen" },
      { name: "Dawg" },
      { name: "Ethan" },
      { name: "George" },
      { name: "Frank" },
      { name: "Hanes" }
    ],
    links: [
      { source: "Alice", target: "Bob" },
      { source: "Chen", target: "Bob" },
      { source: "Dawg", target: "Chen" },
      { source: "Hanes", target: "Frank" },
      { source: "Hanes", target: "George" },
      { source: "Dawg", target: "Ethan" }
    ]
  };

  const simulation = d3 // use d3 to simulate physical force
    .forceSimulation(graph.nodes) // use the force simulation function from d3 to model how nodes interact
    .force("link", d3.forceLink(graph.links).id(d => d.name)) // use the forceLink function to model how links interact
    .force("charge", d3.forceManyBody().strength(-100)) // use the ManyBody function to simulate gravity between nodes
    .force("center", d3.forceCenter(width / 2, height / 2)) // center the "gravitational pull" in the middle of the visualization
    .force("collision", d3.forceCollide(d => 10)); // nodes can't collide with each other and have a 2 pixel pad



  const link = svg // draw the links on the svg
    .append("g") // make all the links html elements called g
    .attr("stroke", "#999") // define the color of the link lines
    .attr("stroke-opacity", 0.6) // define the opacity of the link lines
    .selectAll("line") // select all line objects
    .data(graph.links) // use the links entries from the data to draw the lines
    .join("line") // adjust the lines when something moves, like if we drag a node or there's a collission
    .attr("stroke-width", d => Math.sqrt(d.value)); // make the links as wide as the square root of the value column (this is a good way to scale things if you have a wide range in values).

  const node = svg // draw the nodes on the svg
    .append("g") // make all nodes html elements called g
    .attr("stroke", "#fff") // define the default color of the nodes
    .attr("stroke-width", 1.5) // draw a stroke 1.5px wide around each node
    .selectAll("circle") // select all circle objects
    .data(graph.nodes) // use the nodes entries in the data to draw the circles
    .join("circle") // adjust the nodes when something moves
    .attr("r", d => 10) // draw each node as a circle with the radius of its degree value plus 2px
    .attr("fill", "red") // use the color function defined below to assign a color to each modularity class
    .call(drag(simulation)); // use the drag function defined below to allow us to click and drag nodes.  This can be commented out if you don't want to use the drag function below


  simulation.on("tick", () => {
    link
      .attr("x1", d => d.source.x)
      .attr("y1", d => d.source.y)
      .attr("x2", d => d.target.x)
      .attr("y2", d => d.target.y);

    node.attr("cx", d => d.x).attr("cy", d => d.y);
  });

  function drag(simulation) {
  function dragstarted(event) {
    if (!event.active) simulation.alphaTarget(0.3).restart();
    event.subject.fx = event.subject.x;
    event.subject.fy = event.subject.y;
  }

  function dragged(event) {
    event.subject.fx = event.x;
    event.subject.fy = event.y;
  }

  function dragended(event) {
    if (!event.active) simulation.alphaTarget(0);
    event.subject.fx = null;
    event.subject.fy = null;
  }

  return d3
    .drag()
    .on("start", dragstarted)
    .on("drag", dragged)
    .on("end", dragended);
}
        
    },

    methods: {
        
    },
};
</script>

<style lang="scss" scoped>

</style>