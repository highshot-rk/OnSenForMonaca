//メニュー種類リスト
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
                <p class="practice-toolbar-title text-font-18">メニュー種類リスト</p>
            </div>
            <div class="right" style="width:35%">
                
            </div>
        </v-ons-toolbar>
        <v-ons-card class="card-item" style="margin-top: 2.9rem; margin-bottom: 0;">
            <v-ons-list>
                <v-ons-list-item v-for="menu_type, index in menu_type_list" :key="index"
                     modifier="longdivider" tappable="true"
                >
                    <div class="center"><span>{{menu_type.name}}</span></div>
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
                        @click="addTypeDialogVisible=true;"
            >
                <span style="padding: 1rem;">
                    <v-ons-icon icon="md-plus, material:md-plus-outline"
                                size="1rem" style="height: 0.2rem;"
                    >
                    </v-ons-icon>
                </span>
                <span>新規種類の追加</span>
            </v-ons-button>

            <v-ons-alert-dialog modifier="rowfooter"
            :visible.sync="confirmDeleteDialogVisible"
            >
                <span slot="title" class="dialog-title text-font-17">{{this.menu_type_list[current_selected_type].name}}の削除</span>
                <p class="dialog-text text-font-13">本当に「{{this.menu_type_list[current_selected_type].name}}」を削除しますか？</p> 
                <p class="dialog-text text-font-13">この操作は取り消せません。</p>
                <template slot="footer">
                    <v-ons-alert-dialog-button @click="confirmDeleteDialogVisible = false" class="dialog-button text-font-16">キャンセル</v-ons-alert-dialog-button>
                    <v-ons-alert-dialog-button @click="deleteType" class="dialog-button text-font-16 dialog-delete-button-color">削除</v-ons-alert-dialog-button>
                </template>
            </v-ons-alert-dialog>

            <v-ons-alert-dialog modifier="rowfooter"
            :visible.sync="this.addTypeDialogVisible"
            >
                <span slot="title" class="dialog-title">新規種類の追加</span>
                <v-ons-input class="dialog-text" placeholder="種類の名前"></v-ons-input>
                <template slot="footer">
                    <v-ons-alert-dialog-button
                        @click="addTypeDialogVisible = false;" 
                        class="dialog-button text-font-16"
                    >キャンセル</v-ons-alert-dialog-button>

                    <v-ons-alert-dialog-button 
                        @click="addType" 
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
    name: "MenuTypeList",
    data: function() {
        return {
            menu_type_list:[
                {"name":"Swim"},{"name":"Kick"},{"name":"Pull"}
            ],
            current_selected_type: 0,
            confirmDeleteDialogVisible: false,
            addTypeDialogVisible: false,
        }
    },
    components: {
    },
    props: {
    },
    computed: {
    },
    methods: {
        editType: function () {

        },
        confirmDelete: function (index) {
            this.current_selected_type = index;
            this.confirmDeleteDialogVisible = true;
        },
        deleteType: function () {
            this.confirmDeleteDialogVisible = false;
        },
        addType: function () {
            this.addTypeDialogVisible = false;
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
    .grey_btn{
        background: rgba(0, 0, 0, 0.05);
        border-radius: 6rem;
        padding: 0.4rem 1rem;
        /* margin: 0.2rem 0.5rem 0.5rem 0.5rem; */
    }
    .add_content{
        margin-top:70px;
    }
    .ac-title{
        font-family: "Noto Sans CJK JP";
        font-style: normal;
        font-weight: bold;
        text-align: left;
        color: #193342;
        margin: 0.6rem 0 0.5rem 0;
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