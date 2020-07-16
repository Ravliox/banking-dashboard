<template>
  <div id="dashboard">
    <div class="column">
      <DebitCard />
      <LastSpendings />
    </div>
    <div class="column">
      <LastTransactions />
      <ExpensesIncome />
    </div>
  </div>
</template>

<script>
import DebitCard from '@/components/dashboard-components/DebitCard'
import LastSpendings from '@/components/dashboard-components/LastSpendings'
import LastTransactions from '@/components/dashboard-components/LastTransactions'
import ExpensesIncome from '@/components/dashboard-components/ExpensesIncome'

export default {
  components: {
    DebitCard,
    LastSpendings,
    LastTransactions,
    ExpensesIncome
  }
}
</script>

<style lang="scss">
#dashboard {
  display: flex;
  flex: 1 0 auto;
  padding-top: 0.5em;
}

.column {
  display: flex;
  flex-direction: column;
  width: 50%;
  justify-content: space-around;
  align-items: center;
  padding: 0 2em;

  &:first-child {
    border-right: 1px solid gray;
  }

  & > div {
    flex: 1 0 auto;
  }
}


@media screen and (max-width: 800px) {
  #dashboard {
    flex-direction: column;
    overflow-x: hidden;
    overflow-y: scroll;
    flex: 1 1 auto;
    padding-left: 8px;
    height: 100vh;
    padding-bottom: 120px;
  }

  .column {
    width: 100%;
    padding: 0;

    &:first-child {
      border-right: unset;
    }

    & > div {
      flex: unset;
    }
  }
}
</style>