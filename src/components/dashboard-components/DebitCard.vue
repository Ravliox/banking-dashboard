<template>
    <div id="debit-card">
        <div class="header">
            <h1> Your debit card </h1>
            <div class="options">
                <v-icon color="#045E07" size="32">mdi-eye</v-icon>
                <v-icon color="#045E07" size="32">mdi-plus</v-icon>
            </div>
        </div>
        <div class="card-display">
            <img :src="cardFront">
            <img :src="cardBack">
        </div>
    </div>    
</template>

<script>
export default {
    data() {
        return {
            cardFront: require("@/assets/dashboard/card-front.png"),
            cardBack: require("@/assets/dashboard/card-back.svg")
        }
    }
}
</script>

<style lang="scss" scoped>
#debit-card {
    width: 100%;
    height: 50%;
}

.header {
    width: 100;
    display: flex;
    justify-content: space-between;

    h1 {
        font-size: 1.25em;
        color: #045E07;
    }

    .options {
        i:first-child {
            margin-right: 0.8em;
        }
    }
}

.card-display {
    width: 100%;
    img {
        line-height: 100%;
    }
}
</style>