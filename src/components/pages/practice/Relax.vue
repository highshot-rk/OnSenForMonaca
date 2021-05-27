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
                    <div class="tab-group">
                        <div class="tab active">
                            <div class="face">
                                <img style="width: 1.1rem; height: 1.1rem" src="../../../assets/images/young-boy-01.png" alt="boy">
                            </div>
                            <div class="title">そうた</div>
                        </div>
                        <div class="tab">
                            <div class="face">
                                <img style="width: 1.1rem; height: 1.1rem" src="../../../assets/images/young-girl-01.png" alt="boy">
                            </div>
                            <div class="title">さくら</div>
                        </div>
                    </div>
                    <div class="chart">
                        <template v-for="(mark, key) in marks">
                            <single-chart :key="key" :marks="mark" :max_marks="100" :color1="color1[key]" :color2="color2[key]" :data="data[key]"></single-chart>
                        </template>
                    </div>
                </template>
                <template v-if="key == 1">
                    <div style="position: relative">
                    <img class="main-image" src="../../../assets/images/phone-analysis.png"/>
                    <div class="bar-in-panel">
                        <template v-for="(chartInfo, key) in hChartDataName">
                            <div :key="key" class="h-chart-bar">
                                <div class="name">{{ hChartDataName[key] }}</div>
                                <div class="mark-bar" :style="{background: hChartDataColor[key], width: hChartDataMark[key] / 100 * 5+'rem'}"></div>
                            </div>
                        </template>
                    </div>
                    </div>
                </template>
                <template v-if="key == 2">
                    <img class="last-image" src="../../../assets/images/all-members.png"/>
                    <h6 style="text-align: center">※一度コーチになると役割変更はできません</h6>
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

    export default {
        name: "management-page",
        components: {
            ExTitle,
            ExDescription,
            SingleChart,
        },
        data() {
            return {
                color1: ["#F89E5D", "#F85D95", "#F8CC5D", "#5DF8AD"],
                color2: ["#E2572B", "#E22B6D", "#E2AF2B", "#16CF76"],
                marks: ["70", "100", "60", "30"],
                titles: [
                    "成長の推移がわかります",
                    "練習に参加できます",
                    "一緒に充実して欲しいから",
                ],
                data: ["2/1", "2/12", "2/17", "2/23"],
                descriptions: [
                    "お子様アカウントは３個まで連携が可能です。お子様の成長がまとめて確認できます。",
                    "家のソファから、今どのメニューを何秒で泳いでいるのか確認できます。",
                    "共に泳いでる気持ちで。まずはアカウントを作りましょう！",
                ],
                hChartDataName: [
                    "#1", "#2", "#3", "#4",
                ],
                hChartDataMark: [
                    "90", "50", "80", "100",
                ],
                hChartDataColor: [
                    "orange", "red", "lightblue", "blue",
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
    div.tab-group {
        padding: 2rem 2.2rem;
        display: flex;
        justify-content: center;
    }
    div.tab-group div.tab {
        display: flex;
        justify-content: left;
        border: 1px solid #29B9E7;
        padding: 0.3rem;
        min-width: 6rem;
    }
    div.tab-group div.tab:nth-child(1) {
        border-top-left-radius: 3px;
        border-bottom-left-radius: 3px;
    }
    div.tab-group div.tab:last-child {
        border-top-right-radius: 3px;
        border-bottom-right-radius: 3px;
    }
    div.tab-group div.tab.active {
        background-color: #29B9E7;
        color: white;
    }
    div.tab-group div.tab.active .title {
        color: white;
    }
    div.tab-group div.tab {
        background-color: white;
        color: #29B9E7 !important;
    }
    div.tab-group div.tab .title {
        color: #29B9E7;
    }
    div.title {
        padding: 0.2rem 0rem;
        color: white;
        border-radius: 3px;
        font-size: 1rem;
        width: fit-content;
    }
    div.face {
        padding: 0.35rem;
        width: 1.2rem;
        height: 1.2rem;
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
    .bar-in-panel {
        position: absolute;
        top: 20rem;
        left: 10rem;
    }
    .h-chart-bar {
        display: flex;
        margin-bottom: 0.7rem;
    }
    .bar-in-panel .h-chart-bar .name {
        width: 2.5rem;
    }
    .bar-in-panel .h-chart-bar .mark-bar {
        border-radius: 4px;
    }
</style>
