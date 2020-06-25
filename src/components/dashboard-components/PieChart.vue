<script>
import { Pie } from 'vue-chartjs'

export default {
  extends: Pie,
  props: ['chartdata', 'options'],
  mounted () {
    console.log(this.chartdata)
    this.renderChart(this.chartdata, this.options)
  }
}
</script>

<style>
.pie canvas {
    height: 12em !important;
    width: 20em !important;
}

@media screen and (max-height: 800px) {
    .pie canvas {
        height: 10em !important;
    }
}
</style>