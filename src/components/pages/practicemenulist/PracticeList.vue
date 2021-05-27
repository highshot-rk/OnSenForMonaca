// ウェルカムオファー_コーチ
<template>
    <v-ons-page>
        <v-ons-toolbar class="shadow-1 practice-toolbar card-item">
            <div class="left">
                <v-ons-back-button style="height: 0px;">
                    <v-ons-icon modifier="outline" size="30px" icon="md-arrow-left, material:md-arrow-left-outline"></v-ons-icon>
                </v-ons-back-button>
            </div>
            <!-- </v-ons-col> -->
            <div class="toolbar-title center">練習メニュー一覧</div>
            <div class="right"></div>
        </v-ons-toolbar>

        <div style="margin-top: 3rem;">
            <practice-list-item 
                v-for = "n in 10"
                v-bind:key = "n"
                total-distance = "500" 
                total-time = "4h5m" 
                current-date = "03.17" 
                start-time = "3:30">
            </practice-list-item>
        </div>
        <v-ons-bottom-toolbar class="tool_bottom">
            <div class="tab-bottom">
                <div style="text-align: center">
                <v-ons-button modifier="quiet">
                <span style="width: 18px; height: 18px; margin: 3px;" class='material-icons'>event_note</span>
                <p style="margin: -10px; font-weight: bold;font-size: 10px;">サマリー</p>
                </v-ons-button>
                </div>
                <div style="text-align: center">
                <v-ons-button modifier="quiet" style="color:#8293A3;">
                    <span style="width: 18px; height: 18px; margin: 3px;" class='material-icons'>menu_book</span>
                    <p style="margin: -10px; font-weight: bold; font-size: 10px;">スイムノート</p>
                </v-ons-button>
                </div>
            </div>
        </v-ons-bottom-toolbar>
    </v-ons-page>
</template>

<script>
import PracticeListItem from "./PracticeListItem"
export default {
    name: "practicelist",
    data: function() {
        return {
            // title: '練習メニュー一覧',
        }
    },
    components: {
        PracticeListItem,
    },
    props: [
        
    ],
    computed: {
    },
    methods: {
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
        height: 88px;
    }
    .shadow-1 {
        box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    }
    .toolbar-title {
        font-family: "Noto Sans JP";
        font-style: normal;
        font-weight: bold;
        font-size: 18px;
        color: #303235;
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
    
</style>