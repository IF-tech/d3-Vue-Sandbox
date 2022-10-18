<template>
  <v-app id="inspire">
   

      <v-toolbar-title>Playground || Components, experiments, Demos, tests</v-toolbar-title>

   
    <v-main>
      <v-container fluid>
      <!-- <Simplerectangle></Simplerectangle>
      <DataArray></DataArray>

   
      </v-container>
      <v-container >
        <MinimalForceDirectedGraph></MinimalForceDirectedGraph> -->
        <DraggableNodes></DraggableNodes>
      </v-container>
    </v-main>
  </v-app>
</template>


<script>
import HelloWorld from "./components/HelloWorld";
import Simplerectangle from "./components/simplerectangle.vue";
import DataArray from "./components/DataArray.vue";
import MinimalForceDirectedGraph from "./components/MinimalForceDirectedGraph.vue";
import DraggableNodes from "./components/DraggableNodes.vue";

export default {
  name: 'App',

  components: {
    HelloWorld,
    Simplerectangle,
    DataArray,
    MinimalForceDirectedGraph,
    DraggableNodes
},

  data: () => ({
    methods: {

    },
  }),
};
</script>
