<template>
    <div id="debit-card">
        <div class="header">
            <h1> Your debit card </h1>
            <div class="options">
                <v-btn v-if="!backView" icon @click="switchCardView()"><v-icon color="#045E07" size="32">mdi-eye</v-icon></v-btn>
                <v-btn v-if="backView" icon @click="switchCardView()"><v-icon color="#045E07" size="32">mdi-eye-off</v-icon></v-btn>
                <v-btn icon><v-icon color="#045E07" size="32">mdi-plus</v-icon></v-btn>
            </div>
        </div>
        <div class="card-display">
            <img :src="cardFront" :class="{'hidden': backView}">
            <div class="card-back" :class="{'hidden': !backView}">
                <img :src="cardBack">
                <p class="cvv">556</p>
            </div>
        </div>
        <h1 class="total"> 21, 020 $ USD </h1>
    </div>    
</template>

<script>
export default {
    data() {
        return {
            cardFront: require("@/assets/dashboard/card-front.png"),
            cardBack: require("@/assets/dashboard/card-back.png"),
            backView: false
        }
    },
    methods: {
        switchCardView() {
            this.backView = !this.backView;
        }
    }
}
</script>

<style lang="scss" scoped>
#debit-card {
    width: 100%;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
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
        button:first-child {
            margin-right: 0.8em;
        }
    }
}

.card-display {
    width: 100%;
    display: flex;
    justify-content: center;
    img {
        height: 8.75em;
        margin-top: 1em;
    }

    .card-back {
        position: relative;
        height: 8.75em;
        margin-top: 1em;

        img {
            margin-top: 0;
        }
    }

    .cvv {
        position: absolute;
        bottom: 0;
        right: 1em;
        top: 5em;
        font-weight: bold;
    }

    .hidden {
        display: none;
    }
}

.total {
    font-size: 1em;
    text-align: right;
    margin-top: 1em;
}
</style>