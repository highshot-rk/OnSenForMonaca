// ウェルカムオファー_コーチ
<template>
    <v-ons-page class="page-back-color">
        <v-ons-card class="card-item" style="padding-top: 9rem">
            <div class="until-text">スタートまで</div>
            <circular-count-down-timer
                :initial-value="10"
                :stroke-width="2"
                :steps="10"
                :seconds-stroke-color="'#0099FF99'"
                :minutes-stroke-color="'#0ff'"
                :hours-stroke-color="'#0f0'"
                :underneath-stroke-color="'#ffffffff'"
                :seconds-fill-color="'none'"
                :minutes-fill-color="'#00ff0066'"
                :hours-fill-color="'#ff000066'"
                :size="320"
                :padding="4"
                :hour-label="'hours'"
                :minute-label="'minutes'"
                :second-label="''"
                :show-second="true"
                :show-minute="false"
                :show-hour="false"
                :show-negatives="false"
                :paused="some_variable"
                :notify-every="'second'"
            ></circular-count-down-timer>
            <div style=" max-height: 11rem; overflow: auto">
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
            </div>
            <div class="button-div">
                <v-ons-button class="mx-auto button-long-setting">キャンセル</v-ons-button>
            </div>
        </v-ons-card>
    </v-ons-page>
</template>

<script>
import Clock from 'vue-clock2';
import Vue from 'vue';
import CircularCountDownTimer from "vue-circular-count-down-timer";
Vue.use(CircularCountDownTimer);

export default {
    name: "countdown",
    data: function() {
        return {
            time: '10:40:00',
            tds: 5,
            some_variable:false,
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
        Clock,
        // CircularCountDownTimer
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
        },
        finished: () => {
            console.log('finished');
        },
        updated: (status) => {
            console.log(status);    //{"value": 144, "seconds": 24, "minutes": 2, "hours": 0}
        }
    }
}
</script>

<style scoped>
    
    /*  */
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
        margin: 0;
        width: 100%;
        padding: 0.5rem;
        border-radius: 0.1rem;
        height: calc(100vh);
        overflow: auto;
        background-color: #0089FF;
        color: #FFFFFF;
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
        background: rgba(255, 255, 255, 0.1);
        color: #FFFFFFAA;
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
    .until-text{
        /* スタートまで */

        position: absolute;
        left: 35.73%;
        right: 35.47%;
        top: 24.75%;
        bottom: 71.92%;

        /* 18px JP */
        font-family: "Noto Sans CJK JP";
        font-style: normal;
        font-weight: bold;
        font-size: 18px;
        line-height: 150%;
        /* identical to box height, or 27px */
        text-align: center;

        /* Neutral / White */
        color: #FFFFFF;


    }
    .button-div{
        margin: auto;
        width: fit-content;
        text-align: center;
    }
    .button-long-setting {
        background-color: white;
        border-radius: 30px;
        height: 56px;
        /* left: 28px; */
        mix-blend-mode: normal;
        /* opacity: 0.2; */
        position: relative;
        margin-top: 1rem;
        /* padding-top: .5rem; */
        /* top: 566px; */
        width: 320px;
        border: 0;

        font-family: "Noto Sans CJK JP";
        font-style: normal;
        font-weight: bold;
        font-size: 16px;
        line-height: 150%;
        /* identical to box height, or 24px */
        text-align: center;
        /* Primary / Blue */
        color: #0089FF;
        padding-top: 1rem;
    }
</style>