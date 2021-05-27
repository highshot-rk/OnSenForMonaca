
<template>
    <v-ons-page>
        <v-ons-toolbar class="practice-toolbar">
            <div class="left" style="width:35%">
                <v-ons-back-button>
                    <v-ons-icon modifier="outline" size="30px" icon="md-close, material:md-close-outline"></v-ons-icon>
                </v-ons-back-button>
            </div>
            <!-- </v-ons-col> -->
            <div class="center" style="width:30%">
                <p class="practice-toolbar-title text-font-18">練習の編集</p>
            </div>
            <div class="right" style="width:35%">
                <v-ons-button modifier="quiet" style="color: #5496D7;">
                    <v-ons-icon modifier="outline" size="1.5rem" icon="md-more, material:md-more-outline"></v-ons-icon>
                </v-ons-button>
                <v-ons-button class="practice-toolbar-button">
                    <span>保存</span>
                </v-ons-button>
            </div>
        </v-ons-toolbar>

        <v-ons-card class="card-item" style="margin-top: 2.8rem;">
            <div class="practice-sub-title practice-sub-title-font">
                <span>{{this.practice_time}}</span>
                <v-ons-button modifier="quiet" style="float: right;" class="tool-button" @click="editPracticeInfo">
                    <span><v-ons-icon modifier="outline" icon="md-edit, material:md-edit-outline"></v-ons-icon></span>
                </v-ons-button>
            </div>
        </v-ons-card>
        
        <v-ons-card class="card-item">
            <div class="practice-sub-title practice-etc-font">
                <span style="margin-right:0.4rem">総距離</span>
                <span class="practice-etc-value"  style="margin-right:2rem">{{this.totalDistance}}m</span>
                <span style="margin:0 0.4rem 0 2rem">総時間</span>
                <span class="practice-etc-value">{{this.totalTime}}</span>
            </div>
        </v-ons-card>

        <practice-data-edit-card v-for="datas, index in this.dataList" :key="index"
            :data-list="datas" :number="index"
        >
            <v-ons-card class="card-item" style="margin-top: 0.5rem; border-radius: 0.5rem"
                        @click="addNewMenu(index)"
            >
                <v-ons-button modifier="quiet" class="practice-sub-title" style="text-align: -webkit-center;">
                    <v-ons-icon modifier="outline" icon="md-plus, material:md-plus-outline" size="2rem"
                            class="practice-sub-title practice-add-menu-color"
                    ></v-ons-icon>
                    <span class="practice-sub-title practice-add-menu-font practice-add-menu-color">
                        メニューを追加
                    </span>
                </v-ons-button>
            </v-ons-card>
        </practice-data-edit-card>
    </v-ons-page>
</template>

<script>
import Vue from "vue";
import PracticeNew from "./PracticeNew";
import PracticeDataEditCard from './PracticeDataEditCard.vue';
import PracticeInfoEdit from './PracticeInfoEdit'
Vue.directive('focus', {
    inserted: function (el) {
        // console.log(el.firstChild)
        el.focus();
    },
    update: function (el) {
        Vue.nextTick(function() {
              el.focus();
        })
    }
})
export default {
    name: "practiceedit",
    data: function() {
        return {
            practice_time: "2021/6/30 07:30 - / ロンド成増",
            totalDistance: 4000,
            totalTime: "2h45m",
            dataList: [
                [
                    {"distance": 30, "count": 4, "cycle": "1’0.", "between_sets": 0},
                    {"distance": 50, "count": 2, "cycle": "1’0.", "between_sets": 2},
                    {"distance": 20, "count": 3, "cycle": "1’0.", "between_sets": 1},
                    {"distance": 50, "count": 5, "cycle": "1’0.", "between_sets": 3},
                    {"distance": 60, "count": 1, "cycle": "1’0.", "between_sets": 1},
                ],
                [
                    {"distance": 40, "count": 4, "cycle": "1’0.", "between_sets": 0},
                    {"distance": 70, "count": 2, "cycle": "1’0.", "between_sets": 2},
                    {"distance": 20, "count": 3, "cycle": "1’0.", "between_sets": 1},
                    {"distance": 10, "count": 5, "cycle": "1’0.", "between_sets": 3},
                    {"distance": 40, "count": 1, "cycle": "1’0.", "between_sets": 1},
                ],
                [
                    {"distance": 70, "count": 4, "cycle": "1’0.", "between_sets": 0},
                    {"distance": 510, "count": 2, "cycle": "1’0.", "between_sets": 2},
                    {"distance": 205, "count": 3, "cycle": "1’0.", "between_sets": 1},
                    {"distance": 540, "count": 5, "cycle": "1’0.", "between_sets": 3},
                    {"distance": 20, "count": 1, "cycle": "1’0.", "between_sets": 1},
                ],
                [
                    {"distance": 70, "count": 4, "cycle": "1’0.", "between_sets": 0},
                    {"distance": 230, "count": 2, "cycle": "1’0.", "between_sets": 2},
                    {"distance": 43, "count": 3, "cycle": "1’0.", "between_sets": 1},
                    {"distance": 24, "count": 5, "cycle": "1’0.", "between_sets": 3},
                    {"distance": 663, "count": 1, "cycle": "1’0.", "between_sets": 1},
                ],
            ]
        }
    },
    components: {
        PracticeDataEditCard
    },
    props: {
    },
    computed: {
    },
    methods: {
        removePracticeData: function(index, n){
            this.dataList[index].splice(n,1);
        },
        addPracticeData: function (index) {
            this.dataList[index].push({"distance": 0, "count": 0, "cycle": "1’0.", "between_sets": 0, "status": false})
        },
        addNewMenu: function (index) {
            this.push_screen.push(PracticeNew);
        },
        editPracticeInfo: function(){
            this.push_screen.push(PracticeInfoEdit);
        }
    }
}
</script>

<style scoped>
    .practice-toolbar {
        margin: 0 0 0.5rem 0;
        padding: 3rem 0 0 0;
        text-align: center;
        align-items: center;
        border-radius: 0;
        background-color: white;
        height: 5.4rem;
    }
    .practice-toolbar-title {
        font-family: "Noto Sans JP";
        font-style: normal;
        font-weight: bold;
        color: #303235;
        margin-bottom: 0;
    }
    
    .practice-toolbar-button {
        font-family: "Noto Sans CJK JP";
        font-style: normal;
        font-weight: bold;
        font-size: 12px;
        line-height: 12px;
        text-align: center;
        color: #FFFFFF;
        border-radius: 2rem;
        margin-right: 0.5rem;
        padding: 0.75rem;
        width: 3.7rem;
    }
    .practice-sub-title {
        display: table-cell;
        vertical-align: middle;
        margin: auto;
    }
    .practice-sub-title-font {
        font-family: "SF Pro Display";
        font-style: normal;
        font-weight: normal;
        font-size: 14px;
        line-height: 17px;
        text-align: center;
        color: #5496D7;
    }
    .practice-etc-font {
        font-family: "Noto Sans CJK JP";
        font-style: normal;
        font-weight: normal;
        font-size: 14px;
        line-height: 150%;
        color: #8293A3;
    }
    .practice-etc-value {
        font-family: "SF Pro Text";
        font-style: normal;
        font-weight: normal;
        font-size: 20px;
        line-height: 150%;
        color: #303235;
    }
    .practice-add-menu-font {
        font-family: "SF Pro Display";
        font-style: normal;
        font-weight: normal;
        font-size: 16px;
        line-height: 150%;
    }
    .practice-add-menu-color {
        color: #0089FF;
    }
    .card-item {
        height: 2.9rem; 
        display: table;
        text-align: center;
        margin: 0.2rem 0 0 0;
        width: 100%;
        padding: 0.3rem;
        border-radius: 0.1rem;
    }
    .tool-button {
        margin: -0.5rem 0.5rem;
        padding: 0;
    }
    .dynamic-part {
        display: contents;
    }
    .dynamic-button {
        margin: auto;
        vertical-align: center;
        text-align: center;
    }
    .edit-item-input {
        width: 2rem;
        height: 1rem; 
        margin-top: -0.4rem;
        border-style: none;
        box-shadow: none;
    }
    
</style>