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
            <v-ons-carousel-item :key="key" v-for="(value, key) in titles" style="overflow: auto">
                <ex-title>{{ value }}</ex-title>
                <ex-description>{{ descriptions[key] }}</ex-description>
                <template v-if="key == 0">
                    <img class="main-image" src="../../../assets/images/ex-management-01.png"/>
                </template>
                <template v-if="key == 1">
                    <div class="player-group">
                        <div class="title">チーム A</div>
                        <div class="face">
                            <img style="width: 1.1rem; height: 1.1rem" src="../../../assets/images/young-girl-01.png" alt="boy">
                        </div>
                        <div class="face orange">
                            <img style="width: 1.1rem; height: 1.1rem" src="../../../assets/images/young-boy-01.png" alt="boy">
                        </div>
                        <div class="face">
                            <img style="width: 1.1rem; height: 1.1rem" src="../../../assets/images/young-girl-02.png" alt="boy">
                        </div>
                    </div>
                    <div class="chart">
                        <template v-for="(mark, key) in marks">
                            <single-chart :key="key" :marks="mark" :max_marks="100" :color1="color1[key]" :color2="color2[key]" :data="data[key]"></single-chart>
                        </template>
                    </div>
                </template>
                <template v-if="key == 2">
                    <div class="chart-panel">
                        <!-- <line-chart></line-chart> -->
                        <!-- <img src="../../../assets/images/line-chart.png" width="100%" height="100%" alt=""/> -->
                        <am-chart></am-chart>
                    </div>
                </template>
                <template v-if="key == 3">
                    <img class="last-image" src="../../../assets/images/girl-boy-order.png"/>
                    <h6 style="text-align: center;">※一度コーチになると役割変更はできません</h6>
                    <v-ons-button
                        modifier="large"
                        style="border-radius: 500px;"
                    >コーチアカウントを作成</v-ons-button>
                    <p class="coach-description" style="text-align: center;">すでにアカウントをお持ちの方は<b>こちら</b></p>
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

    // import LineChart from './components/LineChart.vue';
    import ApexChart from './components/ApexChart';
    import AmChart from './components/AmChart';

    export default {
        name: "management-page",
        components: {
            ExTitle,
            ExDescription,
            SingleChart,
            // ApexChart,
            AmChart,
            // LineChart
            // LineChart
        },
        data() {
            return {
                color1: ["#F89E5D", "#F85D95", "#F8CC5D", "#5DF8AD"],
                color2: ["#E2572B", "#E22B6D", "#E2AF2B", "#16CF76"],
                marks: ["70", "100", "60", "30"],
                titles: [
                    "サイクル管理はお任せください",
                    "チーム管理もお任せください",
                    "研究ツールも用意しました",
                    "コーチの本気を見せてやる！",
                ],
                data: ["2/1", "2/12", "2/17", "2/23"],
                descriptions: [
                    "指導に集中できる環境を作ります。ヨーイドン＆タイムの読み上げは、私にお任せください。指導に集中できる環境を作ります。スマホとbluetoothスピーカーを連携すると効果倍増です。",
                    "「頑張っている」がデータでわかる。選手の「努力」を数値化します。データを利用することで、より効果的な声がけが可能です。",
                    "今日のデータ、まとめておきました。全練習のタイム検索、選手スコアの推移の確認、もちろん可能です。",
                    "全ては愛するチームのために。\nまずはアカウントを作りましょう。",
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
                }
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
    .main-image {
        width: 100%;
        margin-top: 4rem;
    }
    div.player-group {
        padding: 2rem 2.2rem;
        display: flex;
        justify-content: space-between;
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
        width: 1.2rem;
        height: 1.2rem;
        background-color: #0089FF;
        border-radius: 100%;
    }
    div.face.orange {
        background-color: #E9A904;
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
    img.last-image {
        width: 100%;
        margin-top: -5rem;
    }
    h6 {
        font-size: 0.9rem;
        color: #0089FF;
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
