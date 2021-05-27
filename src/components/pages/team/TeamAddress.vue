// ウェルカムオファー_コーチ
<template>
    <v-ons-page>
        <div class="mx-auto">
            <v-ons-toolbar class="practice-toolbar">
                <div class="left mx-auto" style="opacity: 0.6">
                    <v-ons-back-button>
                        <v-ons-icon size="1rem" icon="arrow-left, material:arrow-left"></v-ons-icon>
                    </v-ons-back-button>
                </div>
                <div class="center" style="text-align: center; margin-left: 0%">
                    <span class="toolbar-title textlabel-my text-bold-black-18px">{{data.teamname}}</span>
                </div>
            </v-ons-toolbar>
        </div>
        <v-ons-card class="card-item" style="margin-top: 2.9rem; padding-top: 0.2rem">
            <v-ons-list style="background:none; max-height: 84vh; overflow: auto">
                <div class="player-list-title" modifier="nodivider" style="margin-bottom: .5rem; margin-left: .8rem;margin-top: 1rem;">
                    選手一覧
                </div>
                <v-ons-list-item class="player-list-item" style="border-bottom: solid 1px #00000018;">
                    <b-ons-button @click="goToCreate" class="add-member">+ 選手を追加する</b-ons-button>
                </v-ons-list-item>
                <v-ons-list-item v-for="(player, index) in participating_players_list" :key="index"
                    class="player-list-item" style="border-bottom: solid 1px #00000018;"
                >
                        <img :src="player.avatar_src" alt="" class="avatar-md">
                        <div class="mb-2" style="display: inline-block; width: 50vw">
                            <div style="margin-left: 1rem;margin-top: 0rem;display: inline-block">{{player.name}}</div>
                        </div>
                        <div class="mb-2" style="text-align: right; padding-top: .4rem;width: 30%;">
                            <v-ons-button class="linked-text" v-if="not_connected!=index" modifier="quiet"><v-ons-icon size="1rem" icon="fa-link, material:fa-link"></v-ons-icon> 連携済</v-ons-button>
                            <div v-else class="not-linked-text">アカウント未連携</div>
                        </div>
                    <!-- </v-ons-row> -->
                </v-ons-list-item>
                <v-ons-list-item class="player-list-item" style="border-bottom: solid 1px #00000018; padding-bottom: 1.5rem">
                    <b-ons-button @click="goToCreate" class="add-member">+ 選手を追加する</b-ons-button>
                </v-ons-list-item>
            </v-ons-list>
        </v-ons-card>
        <v-ons-bottom-toolbar class="tool_bottom">
            <div class="tab-bottom">
                <div style="text-align: center; opacity: .7;">
                    <v-ons-button modifier="quiet">
                        <span style="width: 18px; height: 18px; margin: 3px;" class='material-icons'>event_note</span>
                        <p style="margin: -10px; font-weight: bold;font-size: 10px;">サマリー</p>
                    </v-ons-button>
                </div>
                <div style="text-align: center">
                    <v-ons-button @click="open_modal()" modifier="quiet" style="color:#8293A3;">
                        <span style="width: 18px; height: 18px; margin: 3px;margin-bottom: .7rem;" class='fa fa-pen'></span>
                        <p style="margin: -7px; font-weight: bold; font-size: 10px;">練習メニュー</p>
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
        <div>
            <v-ons-action-sheet
                :visible.sync="actionSheetVisible"
                cancelable
                title="<span style='font-family: 'Noto Sans JP';
                        font-style: normal;
                        font-weight: bold;
                        font-size: 16px;
                        line-height: 100%;
                        text-align: center;
                        height: 38px;
                        color: #303235;
                        opacity: 1;
                        '>チームA</span>"
            >
                <v-ons-action-sheet-button icon="md-square-o" @click="goToEdit"><span>編集</span></v-ons-action-sheet-button>
                <v-ons-action-sheet-button icon="md-square-o"  @click="open_modal_delete()" modifier="destructive">削除</v-ons-action-sheet-button>
                <v-ons-action-sheet-button icon="md-square-o" @click="close_modal()"><span>キャンセル</span></v-ons-action-sheet-button>
            </v-ons-action-sheet>
            <v-ons-alert-dialog modifier="rowfooter"
                :visible.sync="deleteDialogVisible"
            >
                <span slot="title">チームの削除</span>
                    本当に「Aチーム」<br>を削除しますか？
                <template slot="footer">
                    <v-ons-alert-dialog-button @click="close_modal_delete(false)">キャンセル</v-ons-alert-dialog-button>
                    <v-ons-alert-dialog-button class="delete-button" @click="close_modal_delete(true)">削除</v-ons-alert-dialog-button>
                </template>
            </v-ons-alert-dialog>
        </div>
    </v-ons-page>
</template>

<script>
// import EditTeam from './EditTeam.vue';
import CreateMember from './CreateMember.vue';

export default {
    name: "teamaddress",
    data: function() {
        return {
            checkedValues: Array(this.participating_players_list.length),
            not_connected: 1,
            actionSheetVisible: false,
            deleteDialogVisible: false,
        }
    },
    components: {
    },
    props: {
        "participating_players_list": {
            type: Array,
            default: ()=>[
                {"name":"吉田 花子", "avatar_src":"static/images/swimmer/swimmer01.jpg"},
                {"name":"斎藤 優子", "avatar_src":"static/images/swimmer/swimmer02.jpg"},
                {"name":"村田 隆", "avatar_src":"static/images/swimmer/swimmer03.jpg"},
                {"name":"吉岡 太朗", "avatar_src":"static/images/swimmer/swimmer04.jpg"},
                {"name":"宮下優子", "avatar_src":"static/images/swimmer/swimmer05.jpg"},
                {"name":"佐藤義行", "avatar_src":"static/images/swimmer/swimmer06.jpg"},
                {"name":"村上晴之助", "avatar_src":"static/images/swimmer/swimmer07.jpg"},
                {"name":"鈴木竜也", "avatar_src":"static/images/swimmer/swimmer08.jpg"},
                {"name":"池江璃花子", "avatar_src":"static/images/swimmer/swimmer09.jpg"},
                {"name":"吉田 花子", "avatar_src":"static/images/swimmer/swimmer01.jpg"},
                {"name":"斎藤 優子", "avatar_src":"static/images/swimmer/swimmer02.jpg"},
                {"name":"村田 隆", "avatar_src":"static/images/swimmer/swimmer03.jpg"},
                {"name":"吉岡 太朗", "avatar_src":"static/images/swimmer/swimmer04.jpg"},
                {"name":"宮下優子", "avatar_src":"static/images/swimmer/swimmer05.jpg"},
                {"name":"佐藤義行", "avatar_src":"static/images/swimmer/swimmer06.jpg"},
                {"name":"村上晴之助", "avatar_src":"static/images/swimmer/swimmer07.jpg"},
                {"name":"鈴木竜也", "avatar_src":"static/images/swimmer/swimmer08.jpg"},
                {"name":"池江璃花子", "avatar_src":"static/images/swimmer/swimmer09.jpg"},
            ]
        },
    },
    computed: {
    },
    methods: {
        open_modal() {
            this.actionSheetVisible = true;
        },
        close_modal(){
            this.actionSheetVisible = false;
        },
        open_modal_delete(){
            this.deleteDialogVisible = true;
        },
        close_modal_delete(type){
            this.deleteDialogVisible = false;
            if(type){
                this.close_modal();
                this.$ons.notification.toast('選手を削除しました', {timeout: 2000, modifier: 'my-toast'});
            }
        },
        goToEdit() {
            this.close_modal();
            this.push_screen.push(CreateMember);
        },
        goToCreate() {
            this.push_screen.push(CreateMember);
        }
    }
}
</script>

<style scoped>
    /* @import '/static/global.css'; */
    .practice-toolbar {
        margin: 0 0 0.5rem 0;
        padding: 3rem 0 0 0;
        text-align: center;
        align-items: center;
        border-radius: 0;
        background-color: white;
        border-bottom: solid 3px #EEEEEE55;
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
        margin: 0.2rem 0 0 0;
        width: 100%;
        padding: 0.5rem;
        border-radius: 0.1rem;
        height: calc(100vh - 5.7rem);
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
        background-color: white;
        /* border-top: 1px solid lightgray; */
        border-top-left-radius: 0.5rem;
        border-top-right-radius: 0.5rem;
        height: 5rem;
    }
    .tool_bottom{
        background-color: white;
        height: 5rem;
        padding: 0;
        box-shadow: 0 -1px 7px 5px #eeeeee55;
    }
    .list-item__icon{
        text-align: right;
    }
    .add-member{
        margin-left: 0rem;
        margin-top: 1rem;
        font-family: "Noto Sans JP"-medium;
        font-style: normal;
        font-weight: normal;
        font-size: 16px;
        line-height: 150%;
        color: #0089FF;
    }
    .not-linked-text{
        font-family: "SF Pro Text";
        font-style: normal;
        font-weight: normal;
        font-size: 12px;
        line-height: 150%;
        /* identical to box height, or 18px */
        text-align: right;
        margin-top: .4rem;
        /* Primary / Orange */
        color: #E9A904;
    }
    .linked-text{
        font-family: "SF Pro Text";
        font-style: normal;
        font-weight: normal;
        font-size: 12px;
        line-height: 150%;
        color: #5496D7;
    }
    .delete-button{
        font-family: "SF Pro Text";
        font-style: normal;
        font-weight: normal;
        font-size: 16px;
        /* identical to box height, or 24px */
        text-align: center;
        /* Primary / Red */
        color: #EA3223;
    }
    .practice-toolbar {
        margin: 0 0 0.5rem 0;
        padding: 3rem 0 0 0;
        text-align: center;
        align-items: center;
        border-radius: 0;
        background-color: white;
        /* border-bottom: solid 1px #EEEEEE66; */
        height: 88px;
    }
    .list-item__center .list-item__center{
        padding:  0 !important
    }
</style>