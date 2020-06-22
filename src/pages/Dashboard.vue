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

<style lang="scss" scoped>
#dashboard {
  display: flex;
  flex: 1 0 auto;
}

.column {
  display: flex;
  flex-direction: column;
  width: 50%;
  justify-content: space-between;
  align-items: center;
  padding: 0 2em;

  &:first-child {
    border-right: 1px solid gray;
  }
}
</style>