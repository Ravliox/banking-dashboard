<script>
import { Line } from 'vue-chartjs'

export default {
  extends: Line,
  props: ['chartdata', 'options'],
  mounted () {
      console.log(this.chartdata)
    this.renderChart(this.chartdata, this.options)
  }
}
</script>

<style>
.line canvas {
    height: 12em !important;
    width: 20em !important;

}

@media screen and (max-height: 800px) {
    .line canvas {
        height: 10em !important;
        width: 18em !important;
    }
}
</style>