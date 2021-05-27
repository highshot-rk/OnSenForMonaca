<template>
    <v-ons-page>
        <div style="margin: 0; background: #ffffff">
            <div class="container-my" style="height: 95vh;">    
                <div class="x01 screen">
                    <!-- <div class="systems-bars-status-bar">
                        <div class="right-side-guLxMW">
                            <div class="battery-JmGuJP">
                                <img class="rectangle-9TkRty" src="./img/rectangle-24@2x.svg" />
                                <img class="combined-shape-9TkRty" src="./img/combined-shape-18@2x.svg" />
                                <img class="rectangle-ncMxck" src="./img/rectangle-25@2x.svg" />
                            </div>
                            <img class="wifi-JmGuJP" src="./img/wifi-12@2x.svg" />
                            <img class="mobile-signal-JmGuJP" src="./img/mobile-signal-12@2x.svg" />
                        </div>
                        <div class="left-side-guLxMW">
                            <div class="time-3DGxnf"><img class="x941-fbFuCz" src="./img/9-41-12@2x.svg" /></div>
                        </div>
                    </div>
                    <div class="system-bars-home-indicator-C61RwL">
                        <div class="i-phone-x-home-dicator-on-dark-Oqpus2">
                            <div class="rectangle-24-BUTwl1"></div>
                        </div>
                    </div> -->
                    <div class="button-div">
                        <div class="mt-5 field-input-empty-textarea mx-auto">
                            <div class="input-label-agree medium-black-12px center">利用許諾</div>
                            <div class="text-div-my-textarea">
                                <textarea class="text-input-my-textarea" rows="22" modifier="" placeholder="メールアドレス" v-model="name"></textarea>
                            </div>
                        </div>
                        <v-ons-list-item :key="agrees[0]" tappable>
                            <label class="left">
                                <v-ons-checkbox
                                    input-id="checkbox"
                                    :value="agrees[0]"
                                    v-model="checkedagree"
                                >
                                </v-ons-checkbox>
                            </label>
                            <label class="checkbox-agree text-input--font14" for="checkbox">
                                利用許諾を確認し、同意しました。(必須)
                            </label>
                        </v-ons-list-item>
                    <div class="button-div">
                        <v-ons-button @click="signup" class="bold-white-16px mx-auto button-long-primary-normal-my-agree" :disabled="!isActive">次へ</v-ons-button>
                    </div>
                    </div>
                </div>
                </div>
        </div>
    </v-ons-page>
</template>

<script>

const extend = name => ({ name, extends: Template });

export default {
name: "agree",
components: {
},
data() {
    return {
        name: "",
        password: "",
        password1: "",
        checkedagree: [],
        agrees: ["agree"]
    };
},
computed: {
    isActive(){
        return this.checkedagree.length;
    }
},
methods: {
    signup(){
        
    }
},
created() {
        
},
}
</script>

<style scoped>
    /* @import './css/globals.css';
    @import './css/styleguide.css';
    @import './css/x01.css'; */
    span.back-button__icon{
        display: none !important;
    }
    .input-label-agree {
        background-color: transparent;
        height: auto;
        /* left: 0px; */
        letter-spacing: 0.00px;
        line-height: 18px;
        mix-blend-mode: normal;
        margin-bottom: 1rem;
        position: relative;
        text-align: center;
        font-size: 18px;
        font-weight: bold;
        /* text-shadow: 0px 0px 20px #00000080; */
        /* top: 0px; */
        white-space: nowrap;
        width: auto;
    }
    .text-input-my-textarea {
        background-color: #00000000;
        border-radius: 4px;
        border: none;
        height: fit-content;
        /* padding-bottom: 1rem; */
        /* padding-top: 1rem;
        padding-left: 1.5rem; */
        margin: auto;
        font-size: 14px;
        /* left: 0px; */
        mix-blend-mode: normal;
        /* position: absolute; */
        /* top: 26px; */
        resize: none;
        width: 280px;
        font-family: "Noto Sans CJK JP-Medium" !important;
    }
</style>