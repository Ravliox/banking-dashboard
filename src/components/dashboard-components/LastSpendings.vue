<template>
    <div id="last-spendings">
        <div class="header">
            <h1> Last Spendings </h1>
            <div class="time-period">
                <select name="time-period" id="time-period">
                    <option value="month" selected> Month </option>
                    <option value="day" selected> Day </option>
                    <option value="year" selected> Year </option>
                </select>
                <v-icon>mdi-chevron-down</v-icon>
            </div>
        </div>
        <div class="spending-cards">
            <div class="spending-card">
                <h2> Health </h2>
                <v-icon size="61" color="#000"> mdi-hospital </v-icon>
                <h2> $ 120 </h2>
            </div>
            <div class="spending-card">
                <h2> Food </h2>
                <v-icon size="61" color="#000"> mdi-food </v-icon>
                <h2> $ 250 </h2>
            </div>
            <div class="spending-card">
                <h2> Travel </h2>
                <v-icon size="61" color="#000"> mdi-airplane </v-icon>
                <h2> $ 360 </h2>
            </div>
        </div>
        <p class="history">See history <v-icon size="28">mdi-chevron-down</v-icon></p>
        <button class="add-spendings">ADD SPENDINGS</button>
    </div>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
#last-spendings {
    width: 100%;
    padding-top: 15px;
    display: flex;
    flex-direction: column;
    justify-content: space-around;

    .header {
        width: 100%;
        display: flex;
        justify-content: space-between;
        
        h1 {
            font-size: 1.25em;
            color: #045E07;
        }
  }

  #time-period {
      border: 1px solid #045E07;
      width: 4.8em;
      padding: 2px 10px;
      border-radius: 9px;
      justify-content: center;
      font-size: 1em;

      option {
          text-align: center;
      }
  }

  .time-period {
      i {
          position: relative;
          left: -1em;
      }
  }

  .spending-cards {
      display: flex;
      justify-content: space-between;
      margin-top: 1em;

      .spending-card {
          height: 7.7em;
          border: 2px solid #045E07;
          width: 25%;
          display: flex;
          flex-direction: column;
          justify-content: space-around;
          align-items: center;
          border-radius: 33px;

        h2 {
            font-size: 1em;
        }

        i {
            border: 2px solid #045E07;
            border-radius: 50%;
            padding: 5px;
          }

        i::before {
            position: relative;
            right: -1px;
        }
      }
  }

  .history {
      font-size: 0.8em;
      margin-top: 1em;
      cursor: pointer;
      display: inline-block;
  }

  .add-spendings {
      margin-top: 1em;
      background-color: #045E07;
      width: 100%;
      height: 1.8em;
      border-radius: 13px;
      color: #fff;
  }
}
</style>