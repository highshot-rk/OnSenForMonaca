<template>
    <v-ons-page>
        <div class="container-my" style="height: 95vh;margin: 0;background: #0089FF">
        <!-- <div style="margin: 0; background: #0089FF"> -->
            <div class="container-center-horizontal">
                <div class="mx-auto">
                    <ons-toolbar class="practice-toolbar">
                        <div class="left">
                            <ons-button @click="goToTeam" modifier="quiet" style="color: white">
                                <v-ons-icon size="1rem" icon="md-close, material:md-close"></v-ons-icon>
                            </ons-button>
                        </div>
                        <div class="center textlabel-my text-bold-black-18px" style="color: white">QRコード</div>
                        <div class="right w-2"></div>
                    </ons-toolbar>
                </div>
                <div class="qr-back">
                    <v-ons-dialog
                        style="width: 100%; text-align: center"
                        modifier="qr-modal"
                        cancelable
                        :visible.sync="dialogVisible"
                    >
                        <v-ons-page style="text-align: center;">
                            <v-ons-card style="background-color: white; margin: 0; height: 70vh; text-align: center">
                            <img style="padding: 2rem; padding-bottom: 2rem" src="/static/images/qrcode.png" width="250" height="250" alt="">
                            <div class="qr-description">選手、もしくは選手の親が<br>このQRコードをスキャンすると、<br>アカウントを連携することができます。</div>
                            <v-ons-bottom-toolbar class="tool_bottom">
                                <div class="tab-bottom">
                                    <div style="text-align: center;"></div>
                                    <div class="line-text">
                                        <v-ons-button modifier="quiet" style="padding-left: 5rem">
                                            <span style="width: 18px; height: 18px; margin: 3px; border-radius: 50%"><img src="/static/images/line.png" style="border-radius: 50%" width="50" height="50" alt=""></span>
                                            <p style="margin: -7px; font-weight: bold;font-size: 10px; color: black; opacity: .6">LINE</p>
                                        </v-ons-button>
                                    </div>
                                    <div class="line-text" style="text-align: center;">
                                        <v-ons-button @click="codeCopy" modifier="quiet" style="padding-right: 5rem">
                                            <span style="width: 18px; height: 18px; margin: 3px; border-radius: 50%"><img src="/static/images/copy.png" style="border-radius: 50%" width="50" height="50" alt=""></span>
                                            <p style="margin: -7px; font-weight: bold; font-size: 10px; color: black; opacity: .6">コピー</p>
                                        </v-ons-button>
                                    </div>
                                    <div style="text-align: center;"></div>
                                </div>
                            </v-ons-bottom-toolbar>
                            </v-ons-card>
                        </v-ons-page>
                    </v-ons-dialog>
                </div>
            </div>
        </div>
    </v-ons-page>
</template>

<script>

const extend = name => ({ name, extends: Template });
import TeamSetting from './TeamSetting.vue';

export default {
name: "memberqrcode",
components: {
},
data() {
    return {
        dialogVisible: true,
    };
},
computed: {
    
},
methods: {
    goToTeam() {
        this.push_screen.pop();
        while (this.push_screen.pop().name!=="TeamSetting"&&this.push_screen.length) {}
        this.push_screen.push(TeamSetting);
    },
    codeCopy() {
        this.dialogVisible = false;
    }
},
created() {
},
}
</script>

<style scoped>
    
    /* @import './css/styleguide.css'; */
    
    span.back-button__icon{
        display: none !important;
    }
    .practice-toolbar {
        margin: 0 0 0 0;
        padding: 3rem 0 0 0;
        text-align: center;
        align-items: center;
        border-radius: 0;
        background-color: #0089FF;
        border-bottom: solid 0px #0089FF;
        height: 88px;
        color: white;
    }
    .success-check{
        color: #0075FF;
        text-align: center;
    }
    .success-check-text{
        position: absolute;
        width: 160px;
        height: 60px;
        left: 108px;
        top: 356px;
        /* 20px JP */
        font-family: "Noto Sans CJK JP-medium";
        font-style: normal;
        font-weight: bold;
        font-size: 20px;
        line-height: 150%;
        /* or 30px */
        text-align: center;
        /* Primary/Secondary */
        color: #5496D7;
    }
    .qr-back{
        position: relative;
        background-image: url('/static/images/qr_back.png');
        background-size: contain;
        background-repeat: no-repeat;
        height: 70vh;
        width: 100%;
    }
    .qr-description{
        font-family: "Noto Sans CJK JP-medium";
        font-style: normal;
        font-weight: normal;
        font-size: 14px;
        line-height: 150%;
        align-items: center;
        text-align: center;
        color: #193342;
        margin-top: -1rem;
    }
    .tab-bottom {
        display: flex;
        justify-content: space-around;
        background-color: white;
        border-top: 0px solid lightgray;
        border-top-left-radius: 0rem;
        border-top-right-radius: 0rem;
        height: 10rem;
    }
    .tool_bottom{
        background-color: white;
        height: 10rem;
        padding: 0;
        /* box-shadow: 0 -1px 7px 5px #eeeeee55; */
    }
    .line-text{
        font-family: "SF Pro Display";
        font-style: normal;
        font-weight: normal;
        font-size: 12px;
        line-height: 150%;
        align-items: center;
        color: #8293A3;
    }
</style>