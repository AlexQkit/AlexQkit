<template>
  <div>
    <GChart class="chart" type="ColumnChart" :data="chart" :options="chartOptions" />
  </div>
</template>
<!-- ========================================================== -->
<script>
import { GChart } from "vue-google-charts";
import { mapGetters } from "vuex";
export default {
  name: "Histogram",
  display: "Histogram",
  components: { GChart },
  computed: {
    ...mapGetters(["liveResults"]),
    // function that add the attributes of the graph 
    // return the [attributes of chart],[array of probabilities] 
    chart() {
      let temp = this.liveResults.chart;
      temp.unshift(["state", "Non zero probabilities "]);
      return temp;
    },
    // Options of chart (google chart api options) 
    chartOptions() {
      return {
        title: "Circuit Histogram",
        chartArea: {
          
          width: this.liveResults.chart.length * 50
        },
         vAxis: {
            viewWindow: {
              max:1,
              min:0
            }
        },
      };
    }
  }
};
</script>
<!-- ========================================================== -->
<style scoped>
div {
  max-width: 95%;
}
chart {
  overflow-x: auto;
}
</style>
