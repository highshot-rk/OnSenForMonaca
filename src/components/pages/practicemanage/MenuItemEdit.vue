// メニュー項目の編集
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
                <p class="practice-toolbar-title text-font-18">メニュー項目の編集</p>
            </div>
            <div class="right" style="width:35%">
                
            </div>
        </v-ons-toolbar>
        <v-ons-card class="card-item" style="margin-top: 2.9rem; margin-bottom: 0;">
            <v-ons-row style="margin-top: 2rem" class="mb-1">
                <v-ons-col width="15%" class="col-center">
                    <div class="ac-title text-font-12" style="margin:auto;"><span>種類</span></div>
                </v-ons-col>
                <v-ons-col width="75%" class="col-center">
                    <v-ons-select class="grey_btn" style="width: 100%; "
                        v-model="type"
                    >
                    </v-ons-select>
                </v-ons-col>
                
                <v-ons-col width="10%"  class="col-center">
                    <v-ons-button modifier="quiet" @click="editType" class="tool-button">
                        <span>
                            <v-ons-icon  modifier="outline" icon="md-edit, material:md-edit-outline"></v-ons-icon>
                        </span>
                    </v-ons-button>
                </v-ons-col>
            </v-ons-row>
            <v-ons-row class="mb-1">
                <v-ons-col width="15%" class="col-center">
                    <div class="ac-title text-font-12"><span>種目</span></div>
                </v-ons-col>
                <v-ons-col width="75%" class="col-center">
                    <v-ons-select class="grey_btn" style="width: 100%; float:right;"
                        v-model="swim_event"
                    >
                    </v-ons-select>
                </v-ons-col>
                
                <v-ons-col width="10%" class="col-center">
                    <v-ons-button modifier="quiet" @click="editType" class="tool-button">
                        <span>
                            <v-ons-icon  modifier="outline" icon="md-edit, material:md-edit-outline"></v-ons-icon>
                        </span>
                    </v-ons-button>
                </v-ons-col>
            </v-ons-row>
            <v-ons-row class="mb-1">
                <v-ons-col width="15%" class="col-center">
                    <div class=" ac-title text-font-12"><span>内容</span></div>
                </v-ons-col>
                <v-ons-col width="75%" class="col-center">
                    <v-ons-select class="grey_btn" style="width: 100%; float:right;"
                        v-model="contents"
                    >
                    </v-ons-select>
                </v-ons-col>
                
                <v-ons-col width="10%" class="col-center">
                    <v-ons-button modifier="quiet" @click="editType" class="tool-button">
                        <span>
                            <v-ons-icon  modifier="outline" icon="md-edit, material:md-edit-outline"></v-ons-icon>
                        </span>
                    </v-ons-button>
                </v-ons-col>
            </v-ons-row>

            <v-ons-row class="mb-1">
                <v-ons-col width="20%" class="col-center">
                </v-ons-col>
                <v-ons-col width="80%" class="col-center">
                    <div style="text-align:left;">
                        <span class=" ac-title text-font-12" style="font-weight: normal;">目標タイム</span>
                    </div>
                    <v-ons-row>
                        <v-ons-col width="40%" class="col-center">
                            <span class=" ac-title text-font-16">ベストタイム</span>
                        </v-ons-col>
                        <v-ons-col width="20%" class="col-center">
                            <span>+</span>
                        </v-ons-col>
                            
                        <v-ons-col width="40%" class="col-center">
                            <v-ons-select class="grey_btn" style="width: 100%; float:right;"
                                v-model="contents"
                            >
                            </v-ons-select>
                        </v-ons-col>
                    </v-ons-row>
                </v-ons-col>
                    
            </v-ons-row>

            <v-ons-row class="mb-1">
                <v-ons-col width="15%" class="col-center">
                    <div class=" ac-title text-font-12"><span>強度</span></div>
                </v-ons-col>
                <v-ons-col width="75%">
                    <v-ons-select class="grey_btn" style="width: 100%; float:right;"
                        v-model="strength"
                    >
                    </v-ons-select>
                </v-ons-col>
                
                <v-ons-col width="10%" class="col-center">
                    <v-ons-button modifier="quiet" @click="editType"  class="tool-button">
                        <span>
                            <v-ons-icon  modifier="outline" icon="md-edit, material:md-edit-outline"></v-ons-icon>
                        </span>
                    </v-ons-button>
                </v-ons-col>
            </v-ons-row>
            <v-ons-button class="save-button">
                <span class="text-font-16" style="width:100%;">保存</span>
            </v-ons-button>
        </v-ons-card>
    </v-ons-page>
</template>

<script>
export default {
    name: "MenuItemEdit",
    data: function() {
        return {
            type: "",
            swim_event: "",
            contents: "",
            strength:"",
            target_time: "",
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
</style>