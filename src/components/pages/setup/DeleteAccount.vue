//DeleteAccount
<template>
    <v-ons-page style="height: 100vh">
        <v-ons-toolbar class="setup-toolbar">
            <div class="left" style="width:35%">
                <v-ons-back-button>
                    <v-ons-icon modifier="outline" size="30px" icon="md-close, material:md-close-outline"></v-ons-icon>
                </v-ons-back-button>
            </div>
            <!-- </v-ons-col> -->
            <div class="center" style="width:30%">
                <p class="setup-toolbar-title text-font-18">アカウントの削除</p>
            </div>
            <div class="right" style="width:35%">
                
            </div>
        </v-ons-toolbar>
        <v-ons-card class="card-item" style="margin-top: 2.9rem; margin-bottom: 0;">
            <div class="sub-title text-font-16" style="margin-top:1.5rem;">
                <span class="txt-black">アカウントを削除の際のご注意</span>
            </div>

            <div class="sub-title text-font-16" style="text-align:left">
                <v-ons-row class="txt-red" style="margin-top:2.5rem;">
                    <v-ons-col width="10%" style="text">
                        <v-ons-icon modifier="outline" size="1.8rem" icon="md-info, material:md-info-outline"></v-ons-icon>
                    </v-ons-col>
                    <v-ons-col width="90%">
                        <span>取得してきたデータは全て削除されます</span>
                    </v-ons-col>
                </v-ons-row>
                <v-ons-row class="txt-red" style="margin-top:2.5rem;">
                    <v-ons-col width="10%" class="">
                        <v-ons-icon modifier="outline" size="1.8rem" icon="md-info, material:md-info-outline"></v-ons-icon>
                    </v-ons-col>
                    <v-ons-col width="90%">
                        <span>有料サブスクリプションの設定は、ご利用端末の設定画面から別途解除する必要がございます</span>
                    </v-ons-col>
                </v-ons-row>
                <v-ons-row style="margin-top:0.5rem;">
                    <v-ons-col width="10%" class="">
                    </v-ons-col>
                    <v-ons-col width="90%" style="text-align:left;">
                        <a class="txt-blue" style="text-decoration-line: underline;">環境設定アプリを開く</a>
                    </v-ons-col>
                </v-ons-row>
            </div>

            <div class="sub-title text-font-16 txt-black" style="margin-top:11rem;">
                    <span>本当にアカウントを削除しても</span><br>
                    <span>よろしいですか？</span>
            </div>
            
            <v-ons-button class="action-button red-button" style="bottom:16vh"
                        @click="clicked_delete">
                <span class="text-font-16" style="width:100%;">アカウントを削除</span>
            </v-ons-button>
            <v-ons-button class="action-button blue-button"  style="bottom:8vh"
                        @click="clicked_cancel">
                <span class="text-font-16" style="width:100%;">キャンセルして戻る</span>
            </v-ons-button>
        </v-ons-card>
    </v-ons-page>
</template>

<script>
export default {
    name: "setuppassword",
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
        clicked_delete: function() {
        },
        clicked_cancel: function() {
        },
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
    .action-button {
        position:fixed;
        display: flex;
        width: 80%;
        left: 10%;
        text-align: center;
        padding: 0.7rem;
        border-radius:5rem;
        font-family: "Noto Sans CJK JP";
        font-weight: bold;
    }
    .red-button {
        background: #EA3223;
    }
    .blue-button {
        background-color: #0089FF;
    }
    .sub-title {
        font-family: ""Noto Sans JP"";
        font-style: normal;
        font-weight: normal;
        line-height: 150%;
        margin: 1rem 0.5rem;
    }
    .txt-blue {
        color: #0089FF;
    }
    .txt-black {
        color: #303235;
    }
    .txt-red {
        color: #EA3223;
    }
</style>