//QRコードスキャン02
<template>
    <v-ons-page class="page-item">
        <v-ons-toolbar class="top-toolbar">
            <div class="left" style="width:35%">
                <v-ons-back-button style="color:white;">
                    <v-ons-icon modifier="outline" size="30px" icon="md-close, material:md-close-outline"></v-ons-icon>
                </v-ons-back-button>
            </div>
            <!-- </v-ons-col> -->
            <div class="center" style="width:30%">
                <p class="top-toolbar-title text-font-18">QRコード</p>
            </div>
            <div class="right" style="width:35%">
                
            </div>
        </v-ons-toolbar>
        <div class="parent">
            <img src="static/images/qr_image.png" width="100%" class="image1"/>
            <img src="static/images/qr_mask.png" width="100%" class="image2"/>
            <img src="static/images/qr_rect.png" width="80%" class="image3"/>
        </div>
        
        <v-ons-card class="card-item">
            <div class="description-font m-1 text-font-14">
                <span>選手のQRコードをスキャンすると、</span><br>
                <span>選手と連携することができます。</span>
            </div>
        </v-ons-card>

        <v-ons-alert-dialog modifier="rowfooter" class="alert-dialog-mask"
            :visible.sync="allowDialogVisible"
        >
            <span slot="title" class="dialog-title text-font-16" style="font-weight:bold;">“Swim Lab”がカメラのアクセスを求めています。</span>
            <span class="dialog-text text-font-12">QRコードをスキャンします。</span> 
            <template slot="footer">
                <v-ons-alert-dialog-button @click="cancelRead" class="dialog-button text-font-16">許可しない</v-ons-alert-dialog-button>
                <v-ons-alert-dialog-button @click="readQR" class="dialog-button text-font-16">OK</v-ons-alert-dialog-button>
            </template>
        </v-ons-alert-dialog>
    </v-ons-page>
</template>

<script>
export default {
    name: "qrcode",
    data: function() {
        return {
            allowDialogVisible: true,
        }
    },
    components: {
    },
    computed: {
        
    },
    methods: {
        cancelRead: function(){
            this.allowDialogVisible = false;
            this.push_screen.pop();
        },
        readQR: function(){
            this.allowDialogVisible = false;
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
        background: #0089FF;
        height: 12vh;
        
    }
    .top-toolbar-title {
        font-family: "Noto Sans JP";
        font-style: normal;
        font-weight: bold;
        line-height: 24px;
        color: white;
        margin-bottom: 0;
    }
    
    .page-item {
        height: 100vh;
        margin: 0;
        padding: 0;
        width: 100%;
    }
    .card-item {
        position: absolute;
        bottom: 0;
        text-align: center;
        margin: 0;
        padding: 2.7rem 0 3.8rem 0;
        width: 100%;
        border-radius: 0;
        background-color: white;
    }
    .description-font {
        font-family: "Noto Sans CJK JP";
        font-style: normal;
        font-weight: normal;
        line-height: 180%;
        align-items: center;
        text-align: center;
        color: #193342;
    }
    .m-1 {
        margin: 1rem;
    }
    .parent {
        top: 0;
        left: 0;
    }
    .image1 {
        position: relative;
        top: 0;
        left: 0;
    }
    .image2 {
        position: absolute;
        top: 5vh;
        left: 0;
    }
    .image3 {
        position: absolute;
        top: 14.4vh;
        left: 10vw;
    }
    .dialog-title {
        font-family: "Noto Sans CJK JP";
        font-style: normal;
        line-height: 150%;
        color: black;
        margin: 0 0.6rem;
    }
    .dialog-button {
        font-family: "SF Pro Text";
        font-style: normal;
        font-weight: normal;
        color: #007AFF;
    }
    .alert-dialog-mask {
        background: rgba(0, 0, 0, 0.8);
    }
</style>