<template>
    <v-ons-page class="slide-page">

        <v-ons-carousel
            fullscreen
            swipeable
            auto-scroll
            overscrollable
            :index.sync="carouselIndex"
            style="background: white"
        >
            <v-ons-carousel-item :key="key" v-for="(value, key) in titles">
                <ex-title>{{ value }}</ex-title>
                <ex-description>{{ descriptions[key] }}</ex-description>
                <template v-if="key == 0">
                    <div class="player-group">
                        <div class="face orange">
                            <img style="width: 1.1rem; height: 1.1rem" src="../../../assets/images/young-boy-01.png" alt="boy">
                        </div>
                        <div>
                            <p class="personal-name"></p>
                            <p class="personal-info"></p>
                        </div>
                    </div>
                    <div class="chart">
                        <template v-for="(mark, key) in marks">
                            <single-chart :key="key" :marks="mark" :max_marks="100" :color1="color1[key]" :color2="color2[key]" :data="data[key]"></single-chart>
                        </template>
                    </div>
                </template>
                <template v-if="key == 1">
                    <div class="player-single">
                        <div class="face orange">
                            <img style="width: 3.4rem; height: 3.8rem" src="../../../assets/images/young-boy-01.png" alt="boy">
                        </div>
                        <div>
                            <p class="player-name">あなた</p>
                            <p class="player-description"></p>
                            <p class="player-info">
                                <span class="long"></span>
                                <span class="short"></span>
                            </p>
                        </div>
                    </div>
                    <p style="text-align: left;color: #707070;text-weight: bold;margin-top: 3rem;font-weight: bold;opacity: 0.5">友達</p>

                    <v-ons-card style="display: flex;justify-content: space-between;box-shadow: 0 10px 5px rgb(0 0 0 / 12%);">
                        <template v-for="(user, key) in singleUsers">
                            <single-user :key="key" :user="user"></single-user>
                        </template>
                    </v-ons-card>
                </template>
                <template v-if="key == 2">
                    <img class="last-image" src="../../../assets/images/player-free.png"/>
                    <h6>※一度コーチになると役割変更はできません</h6>
                    <v-ons-button
                        modifier="large"
                        style="border-radius: 500px;"
                    >選手アカウントを作成</v-ons-button>
                    <p class="coach-description">すでにアカウントをお持ちの方は<b>こちら</b></p>
                </template>
            </v-ons-carousel-item>
        </v-ons-carousel>

        <div :style="dots">
            <span
                :index="dotIndex - 1"
                v-for="dotIndex in Object.keys(titles).length"
                :key="dotIndex"
                style="cursor: pointer"
                @click="carouselIndex = dotIndex - 1"
                v-bind:class="{ active: carouselIndex == dotIndex - 1 }"
            >
            {{ carouselIndex === dotIndex - 1 ? '\u25CF' : '\u25CF' }}
            </span>
        </div>
    </v-ons-page>
</template>

<script>
    import ExTitle from './components/ExTitle';
    import ExDescription from './components/ExDescription';

    import SingleChart from './components/SingleChart';

    import SingleUser from './components/SingleUser';

    export default {
        name: "management-page",
        components: {
            ExTitle,
            ExDescription,
            SingleChart,
            SingleUser,
        },
        data() {
            return {
                color1: ["#F89E5D", "#F85D95", "#F8CC5D", "#5DF8AD"],
                color2: ["#E2572B", "#E22B6D", "#E2AF2B", "#16CF76"],
                marks: ["70", "100", "60", "30"],
                titles: [
                    "「努力」を数値化します",
                    "「頑張った」を共有しましょう",
                    "楽しむ準備はできましたか？",
                ],
                data: ["2/1", "2/12", "2/17", "2/23"],
                descriptions: [
                    "「速くなる」のヒントがここに。自分自身を研究できます。",
                    "家族、友人と連携できます。応援してもらう。切磋琢磨する。明日の練習がもっと楽しみになります。",
                    "理想のスイマーになる為に。まずはアカウントを作りましょう！",
                ],
                singleUsers: [
                    {img: "/build/assets/images/young-boy-02.png", color: "#5496D7"},
                    {img: "/build/assets/images/young-girl-01.png", color: "#EA3223"},
                    {img: "/build/assets/images/young-boy-01.png", color: "#38E391"},
                    {img: "/build/assets/images/young-girl-03.png", color: "#29B9E7"},
                ],
                carouselIndex: 0,
                dots: {
                    textAlign: 'center',
                    fontSize: '30px',
                    color: '#0089FF',
                    position: 'absolute',
                    bottom: '40px',
                    left: 0,
                    right: 0
                },
            }
        }
    }
</script>

<style scoped>
    .slide-page {
        height: 90vh;
        width: 86vw;
        margin: 7vw;
    }
    span {
        opacity: 0.3;
    }
    span.active {
        opacity: 1;
    }
    div.player-group {
        padding: 2rem 2.2rem;
        display: flex;
        justify-content: center;
    }
    div.title {
        padding: 0.2rem 1rem;
        color: white;
        background-color: #29B9E7;
        border-radius: 3px;
        font-size: 1rem;
        width: fit-content;
    }
    div.face {
        padding: 0.35rem;
        width: 1.4rem;
        height: 1.4rem;
        background-color: #0089FF;
        border-radius: 100%;
        margin-right: 1rem;
    }
    div.face.orange {
        background-color: #E9A904;
    }
    div p.personal-name {
        width: 24vw;
        height: 0.9rem;
        background: #29B9E7;
        margin: 3px;
        border-radius: 3px;
    }
    div p.personal-info {
        width: 18vw;
        height: 0.9rem;
        background: #29B9E7;
        margin: 3px;
        border-radius: 3px;
    }
    div.chart {
        display: flex;
        justify-content: space-between;
        padding: 2rem 2.2rem;
        margin-top: 5rem;
    }
    div.chart-panel {
        margin-top: 5rem;
    }
    div.player-single {
        display: flex;
        margin-top: 7rem;
    }
    div.player-single .face {
        width: 4rem;
        height: 4rem;
        padding: 0.55rem;
    }
    div.player-single .player-name {
        text-align: left;
        margin: 0;
        font-weight: bold;
    }
    div.player-single .player-description {
        width: 24vw;
        height: 1.5rem;
        background: #29B9E7;
        margin: 3px;
        border-radius: 3px;
    }
    div.player-single .player-info {
        margin: 0.7rem 0 0 0;
    }
    div.player-single .player-info span {
        width: 24vw;
        height: 0.7rem;
        background: #29B9E7;
        margin: 3px;
        border-radius: 3px;
        text-align: left;
    }
    div.player-single .player-info span.long {
        padding-left: 10vw;
        padding-right: 10vw;
    }
    div.player-single .player-info span.short {
        padding-left: 6vw;
        padding-right: 6vw;
    }
    img.last-image {
        width: 100%;
        margin-top: 2rem;
    }
    h6 {
        font-size: 0.9rem;
        color: #0089FF;
        font-weight: lighter;
    }
    button {
        background-color: #0089FF;
        border-radius: 100px;
        color: white;
    }
    .coach-description {
        color: #0089FF;
    }
</style>
