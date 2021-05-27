<template>
    <v-ons-page>
        <div style="margin: 0; background: #ffffff">
            <div class="container-my" style="height: 95vh;">
                <div class="x01 screen">
                    <div class="button-div">
                        <img class="image-C61RwL" src="./img/-----@2x.svg" />
                        <div class=" mx-auto"><button class="mailaddressmailcom-C61RwL">mailaddress@mail.com</button></div>
                        <div class="textlabel-C61RwL">
                            にメールを送信しました。<br />届いたメールから認証を行ってください。
                        </div>
                    </div>
                    <div class="button-div">
                        <v-ons-button @click="signup" class="bold-white-16px mx-auto button-long-primary-normal-my-agree" :disabled="!isActive" v-bind:class="{'button-long-primary-normal-my-active':isActive}">次へ</v-ons-button>
                    </div>
                </div>
                </div>
        </div>
    </v-ons-page>
</template>

<script>

const extend = name => ({ name, extends: Template });

export default {
name: "mailsent",
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
        alert("here")
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
</style>