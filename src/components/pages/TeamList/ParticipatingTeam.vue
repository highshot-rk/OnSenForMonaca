//参加中のチーム
<template>
    <v-ons-page style="height: 100vh">
        <v-ons-toolbar class="top-toolbar">
            <div class="left" style="width:35%">
                <v-ons-back-button>
                    <v-ons-icon modifier="outline" size="30px" icon="md-close, material:md-close-outline"></v-ons-icon>
                </v-ons-back-button>
            </div>
            <!-- </v-ons-col> -->
            <div class="center" style="width:30%">
                <p class="top-toolbar-title text-font-18">参加中のチーム</p>
            </div>
            <div class="right" style="width:35%">
                
            </div>
        </v-ons-toolbar>
        <v-ons-card class="card-item" style="margin-top: 2.9rem;text-align:left;">
            <v-ons-list class="list-content text-font-16">
                <v-ons-list-item class="list-title text-font-12" tappable>チーム一覧</v-ons-list-item>
                
                <v-ons-list-item v-for="team,index in team_list" :key="index" 
                        tappable
                >
                    <div class="left"></div>
                    <div class="center txt-black"><span>{{team.name}}</span></div>
                    <div class="right">
                        <v-ons-button @click="confirmQuit(index)" modifier="quiet" class="list-content text-font-16 txt-red">
                            <span>チームから脱退</span>
                        </v-ons-button>
                    </div>
                </v-ons-list-item>
                
                <v-ins-list-item v-if="team_list.length==0">
                    <div class="center" style="text-align: center; margin: 0.5rem">
                        <span class="list-content text-font-12 txt-gray">チームに参加していません</span>
                    </div>
                </v-ins-list-item>
                
                <v-ons-list-item class="txt-blue" tappable>
                    <div class="left">
                        <v-ons-icon modifier="outline" size="1.4rem" icon="fa-qrcode"></v-ons-icon>
                    </div>
                    <div class="center" @click="clickedJoinTeam">
                        新しいチームに参加（QRカメラ）
                    </div>
                    <div class="right">
                        <v-ons-icon modifier="outline" size="1.4rem" icon="md-chevron-right, material:md-chevron-right-outline"></v-ons-icon>
                    </div>
                </v-ons-list-item>
            </v-ons-list>

            <v-ons-alert-dialog modifier="rowfooter"
                :visible.sync="confirmQuitDialogVisible"
            >
                <span slot="title" class="dialog-font text-font-17" style="font-weight:bold;">チームからの脱退</span>
                <p class="dialog-font text-font-13">本当に
                    {{this.team_list.length>0?this.team_list[current_selected_team].name:""}}
                    から脱退しますか？</p> 
                <p class="dialog-font text-font-13">この操作は取り消せません</p>
                <template slot="footer">
                    <v-ons-alert-dialog-button @click="confirmQuitDialogVisible = false" class="txt-blue dialog-font text-font-16">キャンセル</v-ons-alert-dialog-button>
                    <v-ons-alert-dialog-button @click="quitTeam" class="txt-red dialog-font text-font-16">脱退</v-ons-alert-dialog-button>
                </template>
            </v-ons-alert-dialog>
        </v-ons-card>
    </v-ons-page>
</template>

<script>
import QrCodeScan01 from "./QrCodeScan01"
export default {
    name: "participatingteam",
    data: function() {
        return {
            team_list: [
                {"name": "Aチーム",},
                {"name": "Bチーム",},
                {"name": "Cチーム",},
            ],
            current_selected_team: 0,
            confirmQuitDialogVisible: false,
        }
    },
    components: {
    },
    computed: {
        
    },
    methods: {
        confirmQuit: function(index){
            this.current_selected_team = index;
            this.confirmQuitDialogVisible = true;
        },
        quitTeam: function(){
            this.confirmQuitDialogVisible = false;
            this.team_list.splice(this.current_selected_team,1);
            this.current_selected_team = 0;
            this.$ons.notification.toast('チームから脱退しました', {
                    timeout: 1000,
                    modifier: 'my-toast',
                    animation: 'lift',
                });
        },
        clickedJoinTeam: function(){
            this.push_screen.push(QrCodeScan01);
        }
    }
}
</script>

<style scoped>
    .top-toolbar {
        margin: 0 0 0.5rem 0;
        padding: 3rem 0 0 0;
        text-align: center;
        align-items: center;
        border-radius: 0;
        background-color: white;
        height: 5.4rem;
    }
    .top-toolbar-title {
        font-family: "Noto Sans JP";
        font-style: normal;
        font-weight: bold;
        color: #303235;
        margin-bottom: 0;
    }
    
    .card-item {
        height: 89vh; 
        text-align: center;
        margin: 0.2rem 0 0 0;
        width: 100%;
        padding: 1rem;
        border-radius: 0.1rem;
    }
    .tool-button {
        /* margin-left: 1rem; */
        text-align: right;
        padding: 0;
        float: right;

    }
    .align-center {
        margin: auto;

    }
    
    .text-font-17 {
        font-size: 17px;
        line-height: 22px;
    }
    .text-font-13 {
        font-size: 13px;
        line-height: 16px;
    }
    .list-title {
        font-family: "Noto Sans CJK JP";
        font-style: normal;
        font-weight: bold;
        line-height: 150%;
        color: #193342;
    }
    .list-content {
        font-family: "Noto Sans JP";
        font-style: normal;
        font-weight: normal;
        line-height: 150%;
        color: #303235;
    }
    .txt-red {
        color: #EA3223 !important;
    }
    .txt-black {
        color: #303235 !important;
    }
    .txt-blue {
        color: #0089FF !important;
    }
    .txt-gray {
        color: #8293A3;
    }
    .dialog-font {
        font-family: "SF Pro Text";
        font-style: normal;
        font-weight: normal;
        letter-spacing: -0.408px;
        color: black;
    }
    .center {
        padding: 1rem 0;
    }
    .toast--my-toast{
        background: rgba(48, 50, 53, 0.78);
        margin: 0 1rem 3rem 1rem;
    }
    .toast--my-toast__message{
        font-family: "SF Pro Text";
        font-style: normal;
        font-weight: normal;
        line-height: 150%;
        color: #FFFFFF;
    }
    
</style>