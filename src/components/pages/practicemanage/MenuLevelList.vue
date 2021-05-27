//メニュー強度リスト
<template>
    <v-ons-page style="height: 100vh">
        <v-ons-toolbar class="practice-toolbar">
            <div class="left" style="width:35%">
                <v-ons-back-button>
                    <v-ons-icon modifier="outline" size="30px" icon="md-close, material:md-close-outline"></v-ons-icon>
                </v-ons-back-button>
            </div>
            <!-- </v-ons-col> -->
            <div class="center" style="width:30%">
                <p class="practice-toolbar-title text-font-18">メニュー強度リスト</p>
            </div>
            <div class="right" style="width:35%">
                
            </div>
        </v-ons-toolbar>
        <v-ons-card class="card-item" style="margin-top: 2.9rem; margin-bottom: 0;">
            <v-ons-list>
                <v-ons-list-item v-for="menu_level, index in this.menu_level_list" :key="index"
                                 tappable="true"
                >
                    <div class="left"><span class="left-list text-font-16">{{menu_level.name}}</span></div>
                    <div class="center center-list text-font-12">
                        <p>心拍数</p>
                        <span>~{{menu_level.h_rate}}</span>
                    </div>
                    <div class="right">
                        <v-ons-button modifier="quiet" class="tool-button"
                                    @click="confirmDelete(index)"
                        >
                            <span>
                                <v-ons-icon icon="md-close-circle, material:md-close-circle-outline"
                                            style="background: black; color: #D3D3D3; height:0;"
                                            size="1.5rem"
                                >
                                </v-ons-icon>
                            </span>
                        </v-ons-button>
                    </div>
                </v-ons-list-item>
            </v-ons-list>
            <v-ons-button modifier="quiet" style="float:left; margin-top:1rem;"
                        @click="addLevelDialogVisible=true"
            >
                <span style="padding: 1rem;">
                    <v-ons-icon icon="md-plus, material:md-plus-outline"
                                size="1rem" style="height: 0.2rem;"
                    >
                    </v-ons-icon>
                </span>
                <span>新規強度の追加</span>
            </v-ons-button>

            <v-ons-alert-dialog modifier="rowfooter"
            :visible.sync="confirmDeleteDialogVisible"
            >
                <span slot="title" class="dialog-title text-font-17">{{this.menu_level_list[current_selected_level].name}}の削除</span>
                <p class="dialog-text text-font-13">本当に「{{this.menu_level_list[current_selected_level].name}}」を削除しますか？</p> 
                <p class="dialog-text text-font-13">この操作は取り消せません。</p>
                <template slot="footer">
                    <v-ons-alert-dialog-button @click="confirmDeleteDialogVisible = false" class="dialog-button text-font-16">キャンセル</v-ons-alert-dialog-button>
                    <v-ons-alert-dialog-button @click="deleteLevel" class="dialog-button text-font-16 dialog-delete-button-color">削除</v-ons-alert-dialog-button>
                </template>
            </v-ons-alert-dialog>

            <v-ons-alert-dialog modifier="rowfooter"
            :visible.sync="addLevelDialogVisible"
            >
                <span slot="title" class="dialog-title">新規強度の追加</span>
                <p class="dialog-sub-title text-font-12">名前</p>
                <v-ons-input class="dialog-text grey-btn text-font-17" placeholder="強度の名前"></v-ons-input>
                <p class="dialog-sub-title text-font-12" style="margin-top:1rem">心拍数</p>
                
                <v-ons-row class="left-list" style="color:black;">
                    <v-ons-col width="30%" style="display: table;margin:auto; text-align: right;">
                        <span style="display: table-cell;vertical-align:middle">１分間で</span>
                    </v-ons-col>
                    <v-ons-col width="5%" style="display: table;margin:auto;">
                        <span style="margin:auto;">~</span>
                    </v-ons-col>
                    <v-ons-col width="40%" style="display: table;margin:auto;">
                        <v-ons-input class="dialog-text grey-btn" style=" margin:0;"></v-ons-input>
                    </v-ons-col>
                </v-ons-row>
                <template slot="footer">
                    <v-ons-alert-dialog-button
                        @click="addLevelDialogVisible = false" 
                        class="dialog-button text-font-16"
                    >キャンセル</v-ons-alert-dialog-button>
                    
                    <v-ons-alert-dialog-button 
                        @click="addLevel" 
                        class="dialog-button text-font-16" 
                        style="font-weight: bolder;"
                    >追加</v-ons-alert-dialog-button>
                </template>
            </v-ons-alert-dialog>
        </v-ons-card>
    </v-ons-page>
</template>

<script>
export default {
    name: "menulevellist",
    data: function() {
        return {
            menu_level_list:[
                {"name":"A1", "h_rate":150},
                {"name":"EN1", "h_rate":180},
                {"name":"EN2", "h_rate":160},
            ],
            current_selected_level: 0,
            confirmDeleteDialogVisible: false,
            addLevelDialogVisible: false,
        }
    },
    components: {
    },
    props: {
    },
    computed: {
    },
    methods: {
        confirmDelete: function (index) {
            this.confirmDeleteDialogVisible=true;
            this.current_selected_level=index;
        },
        deleteLevel: function () {
            this.confirmDeleteDialogVisible = false;
        },
        addLevel: function () {
            this.addLevelDialogVisible = false;
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
    .grey-btn{
        background: rgba(0, 0, 0, 0.05);
        border-radius: 6rem;
        padding: 0.2rem 1rem;
        margin-top: 0.5rem;
    }
    .left-list{
        font-family: "Noto Sans CJK JP";
        font-style: normal;
        font-weight: bold;
        line-height: 150%;
        color: #303235;
    }
    .center-list {
        margin-right: 2rem;
        text-align:right;
        display:grid;
        font-family: "Noto Sans CJK JP";
        font-style: normal;
        font-weight: normal;
        color: #193342;
    }
    .align-center {
        margin: auto;

    }
    .save-button {
        position:fixed;
        display: flex;
        bottom: 11vh;
        width: 90%;
        text-align: center;
        margin: auto;
        padding: 0.8rem;
        border-radius:5rem;
        font-family: "Noto Sans CJK JP";
        font-weight: bold;
    }
    .mb-1 {
        margin-bottom: 1rem;
    }
    .col-center {
        text-align:center;
        margin:auto;
    }
    .dialog-sub-title {
        font-family: "Noto Sans CJK JP";
        font-style: normal;
        font-weight: normal;
        line-height: 150%;
        color: #193342;
        text-align: left;
        margin-left: 0.5rem;
    }
    .dialog-text {
        font-family: "SF Pro Text";
        font-style: normal;
        font-weight: normal;
        text-align: center;
        letter-spacing: -0.078px;
        color: #000000;
    }
    .text-font-13 {
        font-size: 13px;
        line-height: 16px;
    }
    .text-font-17 {
        font-size: 17px;
        line-height: 22px;
    }
    .dialog-title {
        font-family: "SF Pro Text";
        font-style: normal;
        font-weight: bolder;
        text-align: center;
        letter-spacing: -0.41px;
        color: #000000;
    }
    .dialog-button {
        font-family: "SF Pro Text";
        font-style: normal;
        font-weight: normal;
        color: #007AFF;
        text-align: center;
    }
    .dialog-delete-button-color {
        color: #EA3223;
    }
</style>