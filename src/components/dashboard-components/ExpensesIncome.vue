<template>
  <div id="expenses-income">
      <div class="header">
        <h1> Expenses/Income </h1>
        <div>
          <select id="chart-time-period">
            <option selected> Oct.1 2020-Oct. 29 2020</option>
          </select>
          <v-icon>mdi-chevron-down</v-icon>
        </div>
      </div>
      <div class="chart-row" :class="{'line': lineSelected, 'pie': !lineSelected}">
        <LineChart v-if="lineSelected" :chartdata="lineChart.datacollection" :options="lineChart.options"/>
        <PieChart v-else :chartdata="pieChart.datacollection" :options="pieChart.options"/>
        <div class="button-collumn">
          <button @click="lineSelected = true" :class="{'selected': lineSelected}"><v-icon>mdi-chart-line</v-icon></button>
          <button @click="lineSelected = false" :class="{'selected': !lineSelected}"><v-icon>mdi-chart-pie</v-icon></button>
        </div>
      </div>
  </div>
</template>

<script>
import LineChart from './LineChart.vue'
import PieChart from './PieChart.vue'

export default {
  components: {
    LineChart,
    PieChart
  },
  data() {
    return {
      lineSelected: true,
      lineChart: {
        datacollection: {
          labels: ["0", "Week1", "Week2", "Week3", "Week4"],
          datasets: [
            {
              label: 'Expenses',
              backgroundColor: 'transparent',
              data: [500, 600, 2000, 1500, 1300],
              cubicInterpolationMode: 'monotone',
              borderColor: "#045E07"
            }, {
              label: 'Income',
              backgroundColor: 'transparent',
              data: [2500, 1000, 1500, 900, 1500],
              cubicInterpolationMode: 'monotone',
              borderColor: "#EBB54B"
            }
          ]
        },
        options: {
          bezierCurve : false,
          elements: {
              line: {
                  tension: 0
              }
          },
          legend: {
            position: 'bottom'
          },
          responsive: true,
          maintainAspectRatio: false,
        }
      },
      pieChart: {
        datacollection: {
          labels: ['Income', 'Expenses'],
          datasets: [{
              data: [60, 40],
              backgroundColor: [ "#EBB54B", "#045E07"]    
          }]
        },
        options: {
          legend: {
            position: 'bottom'
          },
          responsive: true,
          maintainAspectRatio: false
        } 
      }
    }
  }
}
</script>

<style lang="scss">
#expenses-income {
  width: 100%;
  display: flex;
  flex-direction: column;
  .header {
    width: 100%;
    display: flex;
    justify-content: space-between;
    margin-bottom: 0.5em;
    
    h1 {
        font-size: 1.25em;
        color: #045E07;
    }

    div {
      display: flex;
    }
  }

  .chart-row {
    display: flex;
    justify-content: space-between;
    flex: 1 0 auto;

    & > div:first-child {
      flex: 1 0 auto;
      display: flex;
      justify-content: center;
    }

    .button-collumn {
      display: flex;
      flex-direction: column;

      button {
        border: 2px solid #425042;
        border-radius: 4px;
        padding: 3px;
        width: 44px;
        height: 37px;
        margin-top: 3px;

        &.selected {
          border: 2px solid #000;
          background-color: #ECECEC;
          i {
            color: #000 !important;
          }
        }
      }
    }
  }
}

@media screen and (max-width: 800px) {
  #expenses-income {
    margin-top: 15px;

    .header {
      flex-direction: column;
    }

    .chart-row {
      flex-direction: column-reverse;
      .button-collumn {
        flex-direction: row;
        justify-content: center;

        button:first-child {
          margin-right: 5px;
        }

        button:last-child {
          margin-left: 5px;
        }
      }
    }

  }
}
</style>