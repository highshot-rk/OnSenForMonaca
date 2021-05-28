// ウェルカムオファー_コーチ
<template>
    <v-ons-page>
        <v-ons-toolbar class="practice-toolbar">
            <div class="left mx-auto" style="opacity: 0.8">
                <v-ons-back-button>
                    <v-ons-icon size="1.6rem" icon="md-close, material:md-close"></v-ons-icon>
                </v-ons-back-button>
            </div>
            <div class="center" style="text-align: center; margin-left: 0%; margin-top: -8px">
                <span class="toolbar-title">メニュー実施設定</span>
            </div>
        </v-ons-toolbar>
        <div style="margin-top: 0rem;padding: 1rem; padding-top: 0rem">
            <v-ons-list style="background:none">
                <v-ons-list-item v-for="(menu, key) in menu_list" :key="key"
                    style="border-bottom: solid 1px #00000018; padding: .1rem .5rem; padding-right: 0"
                >
                    <div style="width: 30%;" class="name-text">{{menu.name}}</div>
                    <div v-if="menu.type!==2" class="menu-value-text" style="text-align: right; width: 70%;">
                        {{menu.value}}
                        <v-ons-icon v-if="menu.type===1" style="color: #5496D7; margin-left: 1.2rem" size="1.4rem" icon="md-volume-mute, material:md-volume-mute"></v-ons-icon>
                    </div>
                    <div v-else style="text-align: center; width: 100%; margin-top: 1rem">
                        <v-ons-row>
                            <v-ons-col width="40px" style="text-align: center; opacity: .5">
                                <v-ons-icon size="1.5rem" icon="md-volume-mute"></v-ons-icon>
                            </v-ons-col>
                            <v-ons-col style="margin-top: -.4rem;">
                                <v-ons-range track-color="black" v-model="menu.value" style="width: 100%;"></v-ons-range>
                            </v-ons-col>
                            <v-ons-col width="40px" style="text-align: center; opacity: .5">
                                <v-ons-icon size="1.5rem" icon="md-volume-up"></v-ons-icon>
                            </v-ons-col>
                        </v-ons-row>
                    </div>
                </v-ons-list-item>
            </v-ons-list>
            <div class="button-div">
                <v-ons-button class="bold-white-16px mx-auto button-long-primary-normal-my">ベースクロックを設定</v-ons-button>
            </div>
        </div>
    </v-ons-page>
</template>

<script>

export default {
    name: "settingvolume",
    data: function() {
        return {
        }
    },
    components: {
    },
    props: {
        "menu_list": {
            type: Array,
            default: ()=>[
                {"name":"サイクルアウト者のタイム", "value":"無視する", "type":0},
                {"name":"タイム計測", "value":"全て計測する", "type":0},
                {"name":"音でスタート管理", "value":"全て鳴らす", "type":0},
                {"name":"タイム読み上げ", "value":"読み上げる", "type":0},
                {"name":"スタート音", "value":"デフォルト", "type":1},
                {"name":"声: レーン#1", "value":"水戸ミントさん", "type":1},
                {"name":"声: レーン#2", "value":"石滝涼さん", "type":1},
                {"name":"声: レーン#3", "value":"小野さん", "type":1},
                {"name":"スターチ音量", "value":70, "type":2},
                {"name":"読み上げ音量", "value":60, "type":2},
            ]
        },
    },
    computed: {
    },
    methods: {
    }
}
</script>

<style scoped>
    .practice-toolbar {
        padding: 3rem 0 0 0;
        text-align: center;
        align-items: center;
        border-radius: 0;
        background-color: white;
        /* height: 88px; */
        border-bottom: solid 1px #00000012;
    }
    .toolbar-title {
        font-family: "Noto Sans JP";
        font-style: normal;
        font-weight: bold;
        font-size: 18px;
        color: #303235;
        /* margin-bottom: 0; */
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
        padding: 0 1rem;
        height: fit-content;
        border-bottom: 0;
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
        /* text-align: right; */
    }
    .name-text{
        /* サイクルアウト者の タイム */
        font-family: "Noto Sans CJK JP-medium";
        font-style: normal;
        font-weight: normal;
        font-size: 12px;
        line-height: 150%;
        /* or 18px */
        display: flex;
        align-items: center;
        /* Neutral/Gray02 */
        color: #8293A3;
    }
    .menu-value-text{
        font-family: "Noto Sans CJK JP-medium";
        font-style: normal;
        font-weight: normal;
        font-size: 14px;
        line-height: 150%;
        /* identical to box height, or 21px */
        text-align: right;
        /* Neutral / Black */
        color: #303235;
    }
    .button-div{
        margin: auto;
        width: fit-content;
        text-align: center;
        margin-top: 1rem;
    }
    .button-long-primary-normal-my {
        background-color: #0088ff;
        border-radius: 30px;
        height: 56px;
        /* left: 28px; */
        mix-blend-mode: normal;
        /* opacity: 0.2; */
        position: relative;
        margin-top: 5%;
        padding-top: .8rem;
        /* top: 566px; */
        width: 84.5vw;
        border: 0;
    }
    .bold-white-16px {
        color: white;
        font-family: "Noto Sans CJK JP-Bold";
        font-size: 16px;
        font-style: normal;
        font-weight: 700;
        background-color: #0088ff;
    }
</style>