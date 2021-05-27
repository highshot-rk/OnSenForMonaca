
<template>
    <!-- <v-ons-page> -->
        <v-ons-card class="card-item" @click="goto_detail(currentDate,totalDistance,totalTime,startTime)">
            <!-- <v-ons-button> -->
                <v-ons-row vertical-align="center">
                    <v-ons-col width="45%">
                        <div class="practice-date left">
                            <span style="font-size: 22px">{{this.currentDate}} </span>
                            <span style="font-size: 14px;">月</span>
                        </div>
                    </v-ons-col>
                    <v-ons-col width="40%" class="practice-etc-value">
                        <div>
                            <span>総距離</span>
                            <span style="color: #303235;">{{this.totalDistance}}m</span>
                            <span>総時間</span>
                            <span style="color: #303235;">{{this.totalTime}}</span>
                        </div>
                    </v-ons-col>
                </v-ons-row>
                <v-ons-row vertical-align="center">
                    <v-ons-col width="45%">
                        <div class="practice-start-time">
                            <span>{{this.startTime}} -</span>
                            <span>ロンド成増</span>
                        </div>
                    </v-ons-col>
                </v-ons-row>
            <!-- </v-ons-button> -->
        </v-ons-card>
    <!-- </v-ons-page> -->
</template>

<script>
import Practice1 from "./Practice1"
export default {
    name: "practicelistitem",
    data: function() {
        return {
            
        }
    },
    props: [
        "totalDistance",
        "totalTime",
        "currentDate",
        "startTime",
    ],
    
    computed: {
    },
    methods: {
        goto_detail(_date, distance, time, start_time) {
            this.push_screen.push(Practice1);
        },
    }
}
</script>

<style scoped>
    .card-item {
        margin: 0.5rem 0 0.5rem 0;
        text-align: center;
        align-items: center;
    }
    .practice-date {
        text-align: left;
        font-family: "Noto Sans JP";
        font-style: normal;
        font-weight: bold;
        font-size: 18px;
        line-height: 26px;
        text-align: center;
        color: #303235;
    }
    .practice-start-time {
        font-family: "SF Pro Display";
        font-style: normal;
        font-weight: normal;
        font-size: 12px;
        line-height: 14px;
        color: #707070;
    }
    .practice-etc-value {
        margin-left: 1rem;
        /* margin-top: 0.3rem; */
        font-family: "Noto Sans CJK JP";
        font-style: normal;
        font-weight: normal;
        font-size: 12px;
        line-height: 150%;
        color: #8293A3;
    }
</style>