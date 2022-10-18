<template>
      <div>
        <v-container>
            <div id="vis">

            </div>
        </v-container>
    </div>
</template>

<script>
import * as d3 from "d3"
export default {
    name: 'SandboxDataArray',

    data() {
        return {
            
        };
    },

    mounted() {
        let letters = "iftech"
        letters = letters.split("");
        d3.select("#vis").selectAll("div").data(letters).enter().append("div").text((d, i) => i)

        
    },

    methods: {
        
    },
};
</script>

<style lang="scss" scoped>
 
</style>