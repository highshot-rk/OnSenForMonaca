//ParentConnect02
<template>
    <v-ons-page style="height: 100vh">
        <v-ons-toolbar class="setup-toolbar">
            <div class="left" style="width:10%">
                <v-ons-back-button>
                    <v-ons-icon modifier="outline" size="30px" icon="md-arrow-left, material:md-arrow-left-outline"></v-ons-icon>
                </v-ons-back-button>
            </div>
            <!-- </v-ons-col> -->
            <div class="center" style="width:80%">
                <p class="setup-toolbar-title text-font-18">QRコードを読み取って連携</p>
            </div>
            <div class="right" style="width:10%">
                
            </div>
        </v-ons-toolbar>
        <v-ons-card class="card-item" style="margin-top: 2.9rem; margin-bottom: 0;">
            <div class="sub-title text-font-16 txt-blue" style="padding-top: 2rem;">
                <img src="static/images/qr_blue_icon.png" alt="" style="width: 6.5rem;">
                <p>連携の手順</p>
            </div>
            <div class="sub-title text-font-16 txt-black" style="text-align: left;margin:2rem 1rem;">
                <p>1. 選手にQRコードを出してもらいましょう</p>
                <p style="margin:2rem 0">2. お手持ちのアプリでQRコードリーダーを起動</p>
                <v-ons-button class="action-button blue-button"
                            @click="clicked_readqr">
                    <span class="text-font-16" style="width:100%;">QRコードを読み取って連携</span>
                </v-ons-button>
                <p style="margin:2rem 0">3. 読み取ると、連携完了</p>
            </div>
        </v-ons-card>
    </v-ons-page>
</template>

<script>
import QRCodeScan02 from "./QRCodeScan02"
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
        clicked_readqr: function() {
            this.push_screen.push(QRCodeScan02)
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
        display: flex;
        
        width: 100%;
        text-align: center;
        padding: 0.7rem;
        border-radius:5rem;
        font-family: "Noto Sans CJK JP";
        font-weight: bold;
    }
    .blue-button {
        background-color: #0089FF;
    }
    .sub-title {
        font-family: "SF Pro Text";
        font-style: normal;
        font-weight: normal;
        line-height: 150%;
    }
    .txt-blue {
        color: #0089FF;
    }
    .txt-black {
        color: #303235;
    }
</style>