//account
<template>
    <v-ons-page style="height: 100vh">
        <v-ons-toolbar class="setup-toolbar">
            <div class="left" style="width:35%">
                <v-ons-back-button>
                    <v-ons-icon modifier="outline" size="1.5rem" icon="md-arrow-left, material:md-arrow-left-outline"></v-ons-icon>
                </v-ons-back-button>
            </div>
            <!-- </v-ons-col> -->
            
            <div class="center" style="width:30%">
                <p class="setup-toolbar-title text-font-18">アカウント設定</p>
            </div>
            <div class="right" style="width:35%">
                
            </div>
        </v-ons-toolbar>
        <v-ons-card class="card-item" style="margin-top: 2.9rem; margin-bottom: 0;">
            <v-ons-list>
                <v-ons-list-item tappable class="list-color-blue" @click="gotoSetupEmail">
                    <div class="left">
                        <v-ons-icon modifier="outline" size="1.4rem" icon="md-email, material:md-email-outline"></v-ons-icon>
                    </div>
                    <div class="center list-text text-font-16" style="padding: 1.2rem 0.8rem;">
                        <span>メールアドレス変更</span>
                    </div>
                    <div class="right">
                        <v-ons-icon modifier="outline" size="1.4rem" icon="md-chevron-right, material:md-chevron-right-outline"></v-ons-icon>
                    </div>
                </v-ons-list-item>
            
                <v-ons-list-item tappable class="list-color-blue" @click="gotoSetupPassword">
                    <div class="left">
                        <v-ons-icon modifier="outline" size="1.4rem" icon="md-key, material:md-key-outline"></v-ons-icon>
                    </div>
                    <div class="center list-text text-font-16" style="padding: 1.2rem 0.8rem;">
                        <span>パスワード変更</span>
                    </div>
                    <div class="right">
                        <v-ons-icon modifier="outline" size="1.4rem" icon="md-chevron-right, material:md-chevron-right-outline"></v-ons-icon>
                    </div>
                </v-ons-list-item>
            
                <v-ons-list-item tappable class="list-color-red" @click="gotoDeleteAccount">
                    <div class="left">
                        <v-ons-icon modifier="outline" size="1.4rem" icon="md-delete, material:md-delete-outline"></v-ons-icon>
                    </div>
                    <div class="center list-text list-color-red text-font-16" style="padding: 1.2rem 0.8rem;">
                        <span>アカウントを削除</span>
                    </div>
                    <div class="right">
                        
                    </div>
                </v-ons-list-item>
            </v-ons-list>
        </v-ons-card>
    </v-ons-page>
</template>

<script>
import DeleteAccount from './DeleteAccount.vue'
import SetupEmail from "./SetupEmail"
import SetupPassword from './SetupPassword'
export default {
    name: "setupaccount",
    data: function() {
        return {
            
        }
    },
    components: {
    },
    props: {
    },
    computed: {
    },
    methods: {
        gotoSetupEmail: function () {
            this.push_screen.push(SetupEmail)
        },
        gotoSetupPassword: function () {
            this.push_screen.push(SetupPassword)
        },
        gotoDeleteAccount: function () {
            this.push_screen.push(DeleteAccount)
        },
        addLevel: function () {
            this.addLevelDialogVisible = false;
        }
    }
}
</script>

<style scoped>
    .setup-toolbar {
        margin: 0 0 0.5rem 0;
        padding: 3rem 0 0 0;
        text-align: center;
        align-items: center;
        border-radius: 0;
        background-color: white;
        height: 5.4rem;
    }
    .setup-toolbar-title {
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
    .left-list{
        font-family: "Noto Sans CJK JP";
        font-style: normal;
        font-weight: bold;
        line-height: 150%;
        color: #303235;
    }
    .align-center {
        margin: auto;

    }
    .mb-1 {
        margin-bottom: 1rem;
    }
    .col-center {
        text-align:center;
        margin:auto;
    }
    .text-font-13 {
        font-size: 13px;
        line-height: 16px;
    }
    .text-font-17 {
        font-size: 17px;
        line-height: 22px;
    }
    .list-text {
        font-family: "Noto Sans CJK JP";
        font-style: normal;
        font-weight: normal;
        color: #303235;
        letter-spacing: 0.1em;

    }
    .list-color-blue {
        color: #5496D7;;
    }
    .list-color-red {
        color: #EA3223;
;
    }
</style>