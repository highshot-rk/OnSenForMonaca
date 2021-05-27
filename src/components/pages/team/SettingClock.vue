// ウェルカムオファー_コーチ
<template>
    <v-ons-page class="page-back-color">
        <v-ons-toolbar class="practice-toolbar">
            <div class="left" style="opacity: 0.6;width: fit-content">
                <v-ons-back-button icon="arrow-left, material:arrow-left">
                    <v-ons-icon size="1rem" icon="arrow-left, material:arrow-left"></v-ons-icon>
                </v-ons-back-button>
            </div>
            <div class="center mx-auto" style="margin-left: 2rem;margin-top: -.5rem">
                <span class="toolbar-title">ベースクロックが60の時タップ</span>
            </div>
            <div class="right" style="margin-left: 2rem;margin-bottom:.5rem">
                <v-ons-toolbar-button icon="sliders-h, font-awesome:sliders-h" style="opacity: 0.9"></v-ons-toolbar-button>
            </div>
        </v-ons-toolbar>
        <v-ons-card class="card-item" style="margin-top: 2.9rem; padding-top: 0.8rem">
            <!--clock :time="time" color="#0089FF" size="280px"></clock-->
            <svg width="276" height="276" viewBox="0 0 276 276" fill="none" xmlns="http://www.w3.org/2000/svg">
                <circle cx="138" cy="138" r="136" stroke="#0089FF" stroke-width="4"/>
                <line x1="73.744" y1="21.686" x2="74.686" y2="23.256" stroke="#0089FF" stroke-width="4" stroke-linecap="round"/>
                <line x1="2" y1="-2" x2="3.83095" y2="-2" transform="matrix(-0.514496 0.857493 0.857493 0.514496 209 22)" stroke="#0089FF" stroke-width="4" stroke-linecap="round"/>
                <line x1="24.7423" y1="69.3073" x2="26.3146" y2="70.2454" stroke="#0089FF" stroke-width="4" stroke-linecap="round"/>
                <line x1="2" y1="-2" x2="3.83095" y2="-2" transform="matrix(-0.858753 0.51239 0.51239 0.858753 257.008 72)" stroke="#0089FF" stroke-width="4" stroke-linecap="round"/>
                <line x1="6" y1="136" x2="7.83095" y2="136" stroke="#0089FF" stroke-width="4" stroke-linecap="round"/>
                <line x1="270" y1="138" x2="271.831" y2="138" stroke="#0089FF" stroke-width="4" stroke-linecap="round"/>
                <line x1="22.7986" y1="202.078" x2="24.4062" y2="201.201" stroke="#0089FF" stroke-width="4" stroke-linecap="round"/>
                <line x1="2" y1="-2" x2="3.83095" y2="-2" transform="matrix(-0.877991 -0.478677 -0.478677 0.877991 255.119 206.791)" stroke="#0089FF" stroke-width="4" stroke-linecap="round"/>
                <line x1="78.1347" y1="256.495" x2="78.9712" y2="254.866" stroke="#0089FF" stroke-width="4" stroke-linecap="round"/>
                <line x1="2" y1="-2" x2="3.83095" y2="-2" transform="matrix(-0.456883 -0.889527 -0.889527 0.456883 203.664 256.188)" stroke="#0089FF" stroke-width="4" stroke-linecap="round"/>
                <line x1="137" y1="271.831" x2="137" y2="270" stroke="#0089FF" stroke-width="4" stroke-linecap="round"/>
                <line x1="137" y1="6.83105" x2="137" y2="5.0001" stroke="#0089FF" stroke-width="4" stroke-linecap="round"/>
                <circle cx="138" cy="138" r="5" fill="#EA3223"/>
                <line x1="138" y1="136" :x2="''+(138+102*Math.sin(time_round))" :y2="''+(34+102*(1-Math.cos(time_round)))" stroke="#EA3223" stroke-width="4" stroke-linecap="round"/>
            </svg>
            <p class="mt-2 mb-2 clock-text">{{time_count.type===0?'選択した秒からスタート':'カウントダウン中！'}}</p>
            <div class="clock-select mx-auto">
                <v-ons-button v-for="n in 6" :key="n" class="clock-select-each" v-bind:class="{'clock-started': time_count.type===n}" :disabled="time_count.type!==0&&time_count.type!==n" :style="n%3!==0&&'margin-right: .5rem'" @click="time_start(n)">{{time_count.type===n?'リセット':n*10}}</v-ons-button>
            </div>
            <table class="mx-auto" style="text-align: center;width: 100%; padding-bottom: 3rem;">
                <tr class="clock-table-th">
                    <td>セット</td>
                    <td>距離</td>
                    <td>本数</td>
                    <td>サイクル</td>
                    <td>セット間</td> 
                </tr>
                <tr v-for="n in tds" :key="n">
                    <td>#1</td>
                    <td>400</td>
                    <td>1</td>
                    <td>{{"7'0."}}</td>
                    <td>0</td> 
                </tr>
            </table>
        </v-ons-card>
    </v-ons-page>
</template>

<script>
import Clock from 'vue-clock2';

export default {
    name: "settingclock",
    data: function() {
        return {
            time: '10:40:00',
            tds: 5,
            time_count: {type: 0, remaining_hours: 0, remaining_mins: 0, interval: 0,
                timedecount: function(){
                    this.remaining_mins = this.remaining_mins-1;
                    if(this.remaining_mins<0){
                        this.remaining_mins = 59;
                        this.remaining_hours = this.remaining_hours-1;
                        if(this.remaining_hours<0){
                            this.timedecountstop();
                        }
                    }
                },
                timedecountstart: function(type){
                    if(this.interval){
                        this.timedecountstop();
                    }
                    this.type = type;
                    this.remaining_hours = type*10;
                    this.remaining_mins = 0;
                    this.interval = setInterval(()=>{
                        this.timedecount()
                    }, 1000*60/10000);
                },
                timedecountstop: function(){
                    clearInterval(this.interval);
                    this.type = 0;
                    this.remaining_hours = 0;
                    this.remaining_mins = 0;
                    this.interval = 0;
                }
            }
        }
    },
    components: {
        Clock
    },
    computed: {
        time_round(){
            const totalmins = this.time_count.remaining_hours*60+this.time_count.remaining_mins;
            if(this.time_count.type)
                return 2*Math.PI*totalmins/(60)/60;
            return 0;
        }
    },
    methods: {
        time_start(n){
            if(n===this.time_count.type){
                this.time_count.timedecountstop()
                return;
            }
            this.time_count.timedecountstart(n)
        }
    }
}
</script>

<style scoped>
    @import './css/globals.css';
    @import './css/x01.css';
    .practice-toolbar {
        margin: 0 0 0.5rem 0;
        padding: 3rem 0 0 0;
        text-align: center;
        align-items: center;
        border-radius: 0;
        background-color: white;
        height: 88px;
    }
    .toolbar-title {
        font-family: "Noto Sans JP";
        font-style: normal;
        font-weight: bold;
        font-size: 18px;
        color: #303235;
        margin-bottom: 0;
        height: 2.5rem;
    }
    .toolbar-sub-title {
        font-family: "SF Pro Display";
        font-style: normal;
        font-weight: normal;
        font-size: 11px;
        line-height: 13px;
        text-align: center;
        margin-top: 0;
        height: 2rem;
    }
    .card-item {
        text-align: center;
        margin: 0.2rem 0 0 0;
        width: 100%;
        padding: 0.5rem;
        border-radius: 0.1rem;
        height: calc(100vh - 2.7rem - 3rem);
        overflow: auto;
    }
    .player-list-title {
        font-family: "Noto Sans CJK JP";
        font-style: normal;
        font-weight: bold;
        font-size: 12px;
        line-height: 150%;
        display: flex;
        align-items: center;
        color: #193342;
    }
    .player-list-item {
        font-family: "Noto Sans JP";
        font-style: normal;
        font-weight: normal;
        font-size: 16px;
        line-height: 150%;
        color: #303235;
    }
    .avatar-md {
        border-radius: 50%;
        width: 2.5rem;
        height: 2.5rem;
    }
    .tab-bottom {
        display: flex;
        justify-content: space-around;
        padding-top: 1rem;
        padding-bottom: 2rem;
        background: white;
        border-top: 1px solid lightgray;
        border-top-left-radius: 0.5rem;
        border-top-right-radius: 0.5rem;
    }
    .tool_bottom{
        height: 82px;
        padding: 0px 40px;
    }
    .list-item__icon{
        text-align: right;
    }
    .clock-text{
        color: #0089FF;
        font-family: "Noto Sans CJK JP";
        font-size: 16px;
        font-style: normal;
        font-weight: 400;
        line-height: 24px;
        letter-spacing: 0px;
        text-align: center;
        opacity: .8;
    }
    .clock-select{
        display: flex;
        flex-wrap: wrap;
        align-items: stretch;
        margin-left: 1rem;
    }
    .clock-select-each{
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        padding: 8px 12px;

        background: #FFFFFF;
        /* Primary / Blue */
        border: 1px solid #0089FF;
        box-sizing: border-box;
        border-radius: 10px;

        font-family: "SF Pro Display";
        font-style: normal;
        font-weight: bold;
        font-size: 36px;
        line-height: 150%;
        /* identical to box height, or 54px */
        text-align: center;
        /* Primary / Blue */
        color: #0089FF;
        /* Inside Auto Layout */
        flex: none;
        order: 0;
        flex-grow: 0;
        margin: 0px 0px;
        margin-bottom: 1rem;
        width: 30%;
    }
    .clock-table-th{
        padding: 4px 20px;
        width: 375px;
        height: 23px;
        background: rgba(84, 150, 215, 0.11);
        color: #5496D7;
        font-family: "Noto Sans CJK JP";
        font-size: 10px;
        font-style: normal;
        font-weight: 400;
        letter-spacing: 0px;
        text-align: center;
        padding-top: .5rem;
    }
    .clock-table-th td{
        width: 21.1%;
        padding: 0;
        margin-top: .5rem;
        vertical-align: middle;
    }
    table td{
        padding: 1rem;
    }
    .page{
        background-color: white !important;
    }
    .clock-started{
        background: #0089FF;
        color: white;
        font-size: 18px;
    }
</style>