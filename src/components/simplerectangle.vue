<template>
    <div>
        <v-container>
            <div id="vis">

            </div>
        </v-container>
    </div>
</template>
<script src="https://cdnjs.cloudflare.com/ajax/libs/d3/7.6.1/d3.min.js" integrity="sha512-MefNfAGJ/pEy89xLOFs3V6pYPs6AmUhXJrRlydI/9wZuGrqxmrdQ80zKHUcyadAcpH67teDZcBeS6oMJLPtTqw==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
<script>
import * as d3 from 'd3';

export default {
    name: 'SandboxSimplerectangle',

    data() {
        return {

            
        };
    },

    mounted() {
    const width = 800;
    const height = 500;
    const svg = d3.select("#vis").append("svg");
    const g = svg.append("g")

    g.append("rect").attr("width", 10).attr("height", 10).style("fill", "red")

        
    },

    methods: {
    
    },
};
</script>

<style lang="scss" scoped>

</style>