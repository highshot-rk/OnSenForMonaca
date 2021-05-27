<template>
    <div>
        <v-ons-card class="card-item" style="margin-top: 0.5rem; border-radius: 0.5rem">
            <div class="practice-toolbar-title text-font-16" style="text-align: left; margin: 0.5rem 0 0 0.5rem">
                <span>メニュー #{{number+1}}</span>
                <v-ons-button modifier="quiet" style="float:right;" class="tool-button" @click="etcAction(number)">
                    <span><v-ons-icon modifier="outline" size="1.5rem" icon="md-more, material:md-more-outline"></v-ons-icon></span>
                </v-ons-button>
                <v-ons-button modifier="quiet" style="float:right;" class="tool-button" @click="newFavorite(number)">
                    <span><v-ons-icon modifier="outline" size="1.5rem" icon="md-bookmark-outline, material:md-edit-outline"></v-ons-icon></span>
                </v-ons-button>
            </div>
            <v-ons-row>
                <v-ons-col>
                    <div class="card-sub-title">
                        <v-ons-row class="item-row">
                            <v-ons-col class="card-sub-title-1" width="25%">種類</v-ons-col>
                            <v-ons-col class="card-sub-title-1" width="25%">種目</v-ons-col>
                            <v-ons-col class="card-sub-title-1" width="25%">内容</v-ons-col>
                            <v-ons-col class="card-sub-title-1" width="25%">強度</v-ons-col>
                        </v-ons-row>
                        <v-ons-row class="item-row">
                            <v-ons-col class="card-sub-title-2" width="25%">Swim</v-ons-col>
                            <v-ons-col class="card-sub-title-2" width="25%">Choice</v-ons-col>
                            <v-ons-col class="card-sub-title-2" width="25%">Drill</v-ons-col>
                            <v-ons-col class="card-sub-title-2" width="25%">EN1</v-ons-col>
                        </v-ons-row>
                    </div>
                </v-ons-col>
                <v-ons-col width="10%" class="dynamic-button">
                    <v-ons-button modifier="quiet" style="float: right;" class="tool-button" @click="menuItemEdit">
                        <span><v-ons-icon modifier="outline" icon="md-edit, material:md-edit-outline"></v-ons-icon></span>
                    </v-ons-button>
                </v-ons-col>
            </v-ons-row>
            <hr style="opacity: 0.2;">
            <v-ons-list-item modifier="nodivider" expandable :expanded.sync="isCardTableExpanded" style="padding:0;" tappable="true">
                <div class="card-table expandable-content" style="padding: 0;">
                    <v-ons-row>
                        <v-ons-col>
                            <v-ons-row class="item-row">
                                <v-ons-col class="item-header" width="20%">セット</v-ons-col>
                                <v-ons-col class="item-header" width="20%">距離</v-ons-col>
                                <v-ons-col class="item-header" width="20%">本数</v-ons-col>
                                <v-ons-col class="item-header" width="20%">サイクル</v-ons-col>
                                <v-ons-col class="item-header" width="20%">セット間</v-ons-col>
                            </v-ons-row>
                        </v-ons-col>
                        <v-ons-col width="10%"></v-ons-col>
                    </v-ons-row>
                    <v-ons-row class="item-row" v-for="data, n in dataList" :key="n">
                        <v-ons-col>
                            <v-ons-row>
                                <v-ons-col class="item-content" width="20%">#{{n+1}}</v-ons-col>
                                <v-ons-col class="item-content" width="20%">
                                    <span class="edit-item-input item-content">
                                        {{data.distance}}
                                    </span>
                                </v-ons-col>
                                <v-ons-col class="item-content" width="20%">
                                    <span class="edit-item-input item-content">
                                        {{data.count}}
                                    </span>
                                </v-ons-col>
                                <v-ons-col class="item-content" width="20%">
                                    <span class="edit-item-input item-content">
                                        {{data.cycle}}
                                    </span>
                                </v-ons-col>
                                <v-ons-col class="item-content" width="20%">
                                    <span class="edit-item-input item-content">
                                        {{data.between_sets}}
                                    </span>
                                </v-ons-col>
                            </v-ons-row>
                        </v-ons-col>
                        <v-ons-col width="10%" class="dynamic-button">
                            <v-ons-button modifier="quiet" style="float: right;" class="tool-button" @click="removePracticeData(n)">
                                <span>
                                    <v-ons-icon icon="md-close-circle, material:md-close-circle-outline"
                                                style="background: black; color: #D3D3D3; height:0;"
                                    >
                                    </v-ons-icon>
                                </span>
                            </v-ons-button>
                        </v-ons-col>
                    </v-ons-row>
                    <hr style="opacity: 0.2;">
                </div>
                <div class="right" style="display: none"></div>
                <div class="top" style="display: none"></div>
            </v-ons-list-item>
            
            <div style="text-align:left;">
                <v-ons-row>
                    <v-ons-col width="5%">
                    </v-ons-col>
                    <v-ons-col width="5%">
                        <v-ons-button @click="isCardTableExpanded = !isCardTableExpanded" modifier="quiet" class="card-bottom-text">
                            <v-ons-icon modifier="outline" size="30px" :icon="this.icon_status"/>
                        </v-ons-button>
                    </v-ons-col>
                    <v-ons-col>
                        <span class="card-bottom-text">セット数:{{dataList.length}}</span>
                    </v-ons-col>
                </v-ons-row>
            </div>
            <div>
                <v-ons-button modifier="quiet" @click="addPracticeData">
                    <span>
                        <v-ons-icon icon="md-plus-circle-o, material:md-plus-circle-o-outline"
                                    size="2.5rem"
                                    style="color: #5496D7; height:0;"
                        >
                        </v-ons-icon>
                    </span>
                </v-ons-button>
            </div>
        </v-ons-card>
        <slot></slot>
        
        <!-- -----------------  action sheet dialog ------------------------ -->
        <v-ons-action-sheet
            :visible.sync="actionSheetVisible"
            cancelable
            :title="
                `<span style='font-family: 'Noto Sans JP';
                            font-style: normal;
                            font-weight: bold;
                            font-size: 16px;
                            line-height: 150%;
                            text-align: center;
                            color: #303235;'>
                    メニュー #${number+1}
                </span>`"
        >
            <v-ons-action-sheet-button icon="md-square-o"
                @click="editPracticeMenu(current_selected_menu)"
            >編集</v-ons-action-sheet-button>
            <v-ons-action-sheet-button icon="md-square-o" modifier="destructive" 
                @click="confimDeleteMenu(current_selected_menu)"
            >削除</v-ons-action-sheet-button>
            <v-ons-action-sheet-button icon="md-square-o"
                @click="actionSheetVisible=false"
            >キャンセル</v-ons-action-sheet-button>
        </v-ons-action-sheet>
        <!-- ----------------------------------------------------- -->
        <!-- ---------------    delete confirm dialog  ----------------- -->
        <v-ons-alert-dialog modifier="rowfooter"
            :visible.sync="alertDeleteDialogVisible"
            >
            <span slot="title" class="dialog-title">メニューの削除</span>
            <span  class="dialog-text">本当に「メニュー#1」を削除しますか？この操作は取り消せません。</span>
            <template slot="footer">
                <v-ons-alert-dialog-button @click="alertDeleteDialogVisible = false" class="dialog-button">キャンセル</v-ons-alert-dialog-button>
                <v-ons-alert-dialog-button @click="deletePracticeMenu(current_selected_menu)" class="dialog-button dialog-delete-button-color">削除</v-ons-alert-dialog-button>
            </template>
        </v-ons-alert-dialog>
        <!--------------------------------------------------------------- -->
        <!-- ----------------   favorite dialog --------------------------- -->
        <v-ons-alert-dialog modifier="rowfooter"
            :visible.sync="alertFavoriteDialogVisible"
            >
            <span slot="title" class="dialog-title">お気に入りメニューに追加</span>
            <v-ons-input class="dialog-text" placeholder="メニューにタイトルをつけてください"></v-ons-input>
            <template slot="footer">
                <v-ons-alert-dialog-button @click="alertFavoriteDialogVisible = false" class="dialog-button">キャンセル</v-ons-alert-dialog-button>
                <v-ons-alert-dialog-button @click="addFavoriteMenu(current_selected_menu)" class="dialog-button">追加</v-ons-alert-dialog-button>
            </template>
        </v-ons-alert-dialog>
        <!-- --------------------------------------------------------------- -->
    </div>
</template>

<script>
import Vue from "vue"
import MenuItemEdit from "./MenuItemEdit"
Vue.directive('focus', {
    inserted: function (el) {
        el.focus();
    },
    update: function (el) {
        Vue.nextTick(function() {
              el.focus();
        })
    }
})
export default {
    name: "practicedataeditcard",
    data: function() {
        return {
            // dataList: [
            //     {"distance": 30, "count": 4, "cycle": "1’0.", "between_sets": 0},
            //     {"distance": 50, "count": 2, "cycle": "1’0.", "between_sets": 2},
            //     {"distance": 20, "count": 3, "cycle": "1’0.", "between_sets": 1},
            //     {"distance": 50, "count": 5, "cycle": "1’0.", "between_sets": 3},
            //     {"distance": 60, "count": 1, "cycle": "1’0.", "between_sets": 1},
            // ]
            isCardTableExpanded: false,
            actionSheetVisible: false,
            current_selected_menu: -1,
            alertDeleteDialogVisible: false,
            alertFavoriteDialogVisible: false,
        }
    },
    components: {
    },
    props: {
        "number": {
            type: Number,
        },
        "dataList":{
            type: Array,
            default: () => [
                {"distance": 30, "count": 4, "cycle": "1’0.", "between_sets": 0},
                {"distance": 50, "count": 2, "cycle": "1’0.", "between_sets": 2},
                {"distance": 20, "count": 3, "cycle": "1’0.", "between_sets": 1},
                {"distance": 50, "count": 5, "cycle": "1’0.", "between_sets": 3},
                {"distance": 60, "count": 1, "cycle": "1’0.", "between_sets": 1},
            ]
        },

    },
    computed: {
        icon_status: function () {
            return this.isCardTableExpanded ? "md-chevron-up" : "md-chevron-down";
        }
    },
    methods: {
        removePracticeData: function(n){
            this.dataList.splice(n,1);
        },
        addPracticeData: function () {
            this.dataList.push({"distance": 0, "count": 0, "cycle": "1’0.", "between_sets": 0})
        },
        etcAction: function (number) {
            this.actionSheetVisible = true;
            this.current_selected_menu = number;
        },
        newFavorite: function (number) {
            this.alertFavoriteDialogVisible = true;
            this.current_selected_menu = number;

        },
        editPracticeMenu: function (current) {
            // this.actionSheetVisible = false;

        },
        confimDeleteMenu: function () {
            this.actionSheetVisible = false;
            this.alertDeleteDialogVisible = true;

        },
        deletePracticeMenu: function (current) {
            this.alertDeleteDialogVisible = false;

        },
        addFavoriteMenu: function (current) {
            this.alertFavoriteDialogVisible = false;

        },
        menuItemEdit: function (current) {
            this.push_screen.push(MenuItemEdit);
        }
    }
}
</script>

<style scoped>
    
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
    .dialog-text {
        color: #333;
        font-family: "SF Pro Text";
        font-weight: Regular;
        font-size: 13px;
    }
    .dialog-title {
        color: #333;
        font-family: "SF Pro Text";
        font-weight: bold;
        font-size: 17px;
    }
    .dialog-button {
        font-family: "SF Pro Text";
        font-style: normal;
        font-weight: normal;
        font-size: 16px;
        color: #007AFF;
    }
    .dialog-delete-button-color {
        color: #EA3223;
    }

    .card-sub-title {
        margin: 0.5rem 0.1rem;
        padding: 0.2rem 0;
        background: #F1F7FC;
        border-radius: 4px;
    }
    .card-sub-title-1 {
        font-family: "Noto Sans JP";
        font-style: normal;
        font-weight: normal;
        font-size: 12px;
        line-height: 150%;
        text-align: center;
        color: #8293A3;
    }
    .card-sub-title-2 {
        font-family: "SF Pro Display";
        font-style: normal;
        font-weight: normal;
        font-size: 14px;
        line-height: 17px;
        text-align: center;
        color: #5496D7;
    }
    .card-table {
        margin: 0.5rem 0.1rem;
    }
    .item-header {
        font-family: "Noto Sans JP";
        font-style: normal;
        font-weight: normal;
        font-size: 12px;
        line-height: 150%;
        text-align: center;
        color: #8293A3;

    }
    .item-row {
        margin: 0.2rem 0;
    }
    .item-content {
        padding: 0.3rem 0;
        font-family: "SF Pro Display";
        font-style: normal;
        font-weight: bold;
        font-size: 14px;
        line-height: 17px;
        text-align: center;
        color: #5496D7;
        background: #F1F7FC;
        box-shadow: inset -0.5px 0px 0px rgba(84, 150, 215, 0.5);
    }
    .card-bottom-text {
        margin: 0;
        padding: 0;
        text-align: left;
        color: #0089FF;
        vertical-align: center;
        font-family: "SF Pro Display";
        font-style: normal;
        font-weight: normal;
        font-size: 16px;
        line-height: 150%;
    }

</style>