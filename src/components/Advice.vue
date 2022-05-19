<template>

    <div class="card">
        <div v-if="adviceId != null">
            <div class="title">
                Advice #{{ adviceId }}
            </div>
        </div>
        <div class="advice">
            {{ advice }}
        </div>
    </div>
    <br />
    <br />
    <div class="divider"></div>
    <br />
    <br />
    <br />
    <div @click="generateAdvice" class="dot">
    </div>
</template>

<script>
export default {
    name: 'Advice',
    data() {
        return {
            adviceId: null,
            advice: null,
            // adviceNumber: null
        }
    },
    methods: {
        async generateAdvice() {
            let url = 'https://api.adviceslip.com/advice'

            let response = await fetch(url, { cache: "no-cache" })
            let slip = await response.json()
            let data = slip.slip

            this.advice = data.advice
            this.adviceId = data.id
        }
    },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Manrope:wght@800&display=swap');

.card {
    height: 400px;
    background: hsl(217, 19%, 24%);
    border-radius: 10px;
    padding: 10px;
    width: 325px;
    margin-left: auto;
    margin-right: auto;
    margin-top: 100px;
}

.title {
    font-size: 20px;
    color: hsl(150, 100%, 66%);
    text-align: center;
}

.advice {
    color: white;
    font-size: 28px;
    padding: 10px;
    text-align: center;
}

.dot {
    height: 50px;
    width: 50px;
    background-color: hsl(150, 100%, 66%);
    border-radius: 50%;
    background-image: url("../assets/icon-dice.svg");
    background-repeat: no-repeat;
    background-position: center;
    display: block;
    margin-left: auto;
    margin-right: auto;
    margin-top: -25px;
}

.divider {
    width: 295px;
    height: 16px;
    background-image: url("../assets/pattern-divider-mobile.svg");
    background-repeat: no-repeat;
    display: block;
    margin-right: auto;
    margin-left: auto;
    margin-top: -125px;
}

body {
    background-color: hsl(218, 23%, 16%);
    font-family: 'Manrope', sans-serif;
}

@media only screen and (min-width: 768px) {
    .card {
        height: 350px;
        background: hsl(217, 19%, 24%);
        border-radius: 10px;
        padding: 10px;
        width: 650px;
        margin-left: auto;
        margin-right: auto;
        margin-top: 100px;
    }

    .divider {
        width: 444px;
        height: 16px;
        background-image: url("../assets/pattern-divider-desktop.svg");
        background-repeat: no-repeat;
        display: block;
        margin-right: auto;
        margin-left: auto;
        margin-top: -125px;
    }
}
</style>