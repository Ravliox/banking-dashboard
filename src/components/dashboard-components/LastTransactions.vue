<template>
  <div id="last-transactions">
    <div class="header">
      <h1> Last Transactions </h1>
      <span> History </span>
    </div>
    <div class="rows">
      <div class="row" v-for="(transaction, index) in transactions" :key="index">
        <div class="image-container">
          <img class="user-photo" :src="transaction.photo">
          <div class="transaction-column">
            <p class="name">{{ transaction.name }} </p>
            <p class="phone-number">{{ transaction.phoneNumber }} </p>
          </div>
        </div>
        <div class = "transaction-column">
          <p class="amount">{{ transaction.amount }} </p>
          <p class="date">{{ transaction.date }} </p>
        </div>
      </div>
    </div>
    <div class="send-money">
      <h2> Send Money </h2>
      <div class="image-row">
        <img class="user-photo" v-for="(user, index) in users" :key="index" :src="user">
        <div class="user-photo">+</div>
      </div>
      <div class="input-row">
        <v-text-field label="Amount" class="amount-input"/>
        <select id="currency" class="currency">
          <option selected>$ USD</option>
          <option>€ EUR</option>
          <option>£ GBP</option>
        </select>
        <label class="currency-label" for="currency"><v-icon>mdi-chevron-down</v-icon></label>
      </div>
      <button class="send-money-button">SEND MONEY</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      transactions: [
        {
          photo: require("@/assets/dashboard/stock1.jpg"),
          name: "Mario Noah",
          phoneNumber: "081 252 333",
          amount: "$ 350",
          date: "10/06"
        },
        {
          photo: require("@/assets/dashboard/stock4.jpg"),
          name: "Taxi",
          phoneNumber: "081 252 333",
          amount: "$ 50",
          date: "10/04"
        }        
      ],
      users: [
        require("@/assets/dashboard/stock1.jpg"),
        require("@/assets/dashboard/stock2.jpg"),
        require("@/assets/dashboard/stock3.jpg"),
        require("@/assets/dashboard/stock4.jpg")      
      ]
    }
  }
}
</script>

<style lang="scss">
#last-transactions {
  width: 100%;

  .header {
    width: 100%;
    display: flex;
    justify-content: space-between;

    span {
      display: flex;
      align-items: center;
      font-size: 0.8em;
      padding: 5px;
      border: 1px solid #045E07;
      width: 4.5em;
      border-radius: 9px;
      justify-content: center;
    }
    
    h1 {
        font-size: 1.25em;
        color: #045E07;
    }
  }

  .user-photo {
    width: 2.2em;
    height: 2.2em;
    border-radius: 50%;
    margin-right: 0.5em;
    border: 2px solid #045E07;
  }

  div.user-photo {
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: #ECECEC;
    color: #045E07;
  }

  .row {
    display: flex;
    justify-content: space-between;
    margin-top: 1em;
    font-size: 0.8em;
    padding: 0 10px;

    .image-container {
      display: flex;
    }

    .name, .amount {
      font-weight: bold;
    }
  }

  .send-money {
    width: 100%;

    &-button {
      margin-top: 0.1em;
      background-color: #045E07;
      width: 100%;
      height: 1.8em;
      border-radius: 13px;
      color: #fff;
    }

    h2 {
      color: #045E07;
      font-size: 0.9em;
      margin-top: 0.5em;
      margin-bottom: 0.5em;
    }

    .image-row {
      display: flex;

      .user-photo {
        cursor: pointer;
      }
    }

    .input-row {
      display: flex;
      width: 100%;
      justify-content: space-around;
    }

    .amount-input {
      label {
        color: #000 !important;
        font-weight: bold !important;
      }
    }

    .currency {
      font-weight: bold;
      outline: 0;

      &-label {
        display: flex;
      }
    }

    .label[for="currency"] {
      vertical-align: center;
    }
  }
}
</style>