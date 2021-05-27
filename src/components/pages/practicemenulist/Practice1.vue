
<template>
    <v-ons-page>
        <v-ons-toolbar class="practice-toolbar">
            <div class="left">
                <v-ons-back-button>
                    <v-ons-icon modifier="outline" size="30px" icon="md-arrow-left, material:md-arrow-left-outline"></v-ons-icon>
                </v-ons-back-button>
            </div>
            <!-- </v-ons-col> -->
            <div class="center">
                <p class="toolbar-title">2021.03.17月の練習</p>
                <p class="toolbar-sub-title">07:30 - / ロンド成増</p>
            </div>
            <div class="right">
                <v-ons-toolbar-button>
                    <v-ons-icon modifier="outline" size="30px" icon="md-download, material:md-download-outline"></v-ons-icon>
                </v-ons-toolbar-button>
            </div>
        </v-ons-toolbar>

        <v-ons-card class="card-item" style="margin-top: 2.9rem; padding-top: 0.2rem">
            <div style="margin-top: 0;">
                <span class="participant">参加者</span>
            </div>
            <div>
                <img v-for="user, index in this.user_list" :src=user.avatar_src :key=index :style="{'z-index': index}"
                     class="avatar-md ml--1" width="28" height="28">
            </div>
        </v-ons-card>
        <v-ons-row>
            <v-ons-col>
                <v-ons-card class="card-item">
                    <div class="participant">
                        <p>総距離</p>
                        <p>{{this.totalDistance}}m</p>
                    </div>
                </v-ons-card>
            </v-ons-col>
            <v-ons-col>
                <v-ons-card class="card-item">
                    <div class="participant">
                        <p>総時間</p>
                        <p>{{this.totalTime}}</p>
                    </div>
                </v-ons-card>
            </v-ons-col>
        </v-ons-row>
        
        <v-ons-card class="card-item">
            <v-ons-carousel swipeable overscrollable 
                item-width="30%" style="padding: 0"
            >
                <v-ons-carousel-item v-for="(item, index) in this.items" :key="index" class="carousel-list">
                    <img :src=item width="100%" style="margin:0.5rem 0;">
                </v-ons-carousel-item>
                <v-ons-carousel class="carousel-list">
                </v-ons-carousel>
            </v-ons-carousel>
        </v-ons-card>

        <!--             menu list                -->
        <practice-menu-list-item v-for="n in 3" :key="n" :number="n"></practice-menu-list-item>
        <!--------------------------------------- -->
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
import PracticeMenuListItem from './PracticeMenuListItem';
export default {
    name: "practice1",
    data: function() {
        return {
            // title: '練習メニュー一覧',
            user_list: [
                {"avatar_src":"static/images/swimmer/swimmer01.jpg"},
                {"avatar_src":"static/images/swimmer/swimmer02.jpg"},
                {"avatar_src":"static/images/swimmer/swimmer03.jpg"},
                {"avatar_src":"static/images/swimmer/swimmer04.jpg"},
                {"avatar_src":"static/images/swimmer/swimmer05.jpg"},
                {"avatar_src":"static/images/swimmer/swimmer06.jpg"},
                {"avatar_src":"static/images/swimmer/swimmer07.jpg"},
                {"avatar_src":"static/images/swimmer/swimmer08.jpg"},
                {"avatar_src":"static/images/swimmer/swimmer09.jpg"},
            ],
            items: [
                "static/images/practice/practice01.png",
                "static/images/practice/practice02.png",
                "static/images/practice/practice03.png",
                "static/images/practice/practice04.png",
                "static/images/practice/practice05.png",
                "static/images/practice/practice06.png",
                "static/images/practice/practice07.png",
                "static/images/practice/practice08.png",
            ]
        }
    },
    components: {
        PracticeMenuListItem,
    },
    props: {
        "totalDistance": {
            type: Number,
            default: 4000
        },
        "totalTime": {
            type: String,
            default: "2h 45m"
        }
    },
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
    }
    .participant {
        margin: auto;
        font-family: "Noto Sans CJK JP";
        font-style: normal;
        font-weight: normal;
        font-size: 14px;
        line-height: 150%;
        color: #8293A3;
    }
    .avatar-md {
        border-radius: 50%;
        border: white;
        border-style: solid;
        border-width: 1px;
    }
    .ml--1 {
        margin-left: -0.3rem;
    }
    .carousel-list {
        margin-left: 0.2rem;
        margin-right: 0.2rem;
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