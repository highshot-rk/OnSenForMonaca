<template>
    <v-ons-page>
        <div style="margin: 0; background: #ffffff">
            <div class="container-my" style="height: 95vh;">
                <div class="mx-auto">
                    <ons-toolbar class="practice-toolbar" style="background-color: white;">
                        <div class="left" style="opacity: 0.6">
                            <ons-back-button>
                                <v-ons-icon size="1rem" icon="arrow-left, material:arrow-left"></v-ons-icon>
                            </ons-back-button>
                        </div>
                        <div class="center textlabel-my text-bold-black-18px">ログイン</div>
                        <div class="right w-2"></div>
                    </ons-toolbar>
                </div>
                <div class="x01 screen">
                    <div class="mt-5 field-input-empty mx-auto" style="margin-top: 6rem">
                        <div class="input-label medium-black-12px mb-1">メールアドレスを入力</div>
                        <input class="text-input-my" type="email" modifier="font14" placeholder="メールアドレス" v-model="name" validated>
                    </div>
                    <div class="field-input-empty mx-auto">
                        <div class="input-label medium-black-12px mb-1">パスワード</div>
                        <input class="text-input-my pt-2 pl-3" type="password" modifier="font14" placeholder="パスワードを入力" v-model="password">
                    </div>
                    <div class="textlabel-VMr6Om medium-dove-gray-12px">
                        <a><span class="span0-alc9Ql medium-dove-gray-12px">パスワード忘れた方はこちら</span></a>
                    </div>
                    <div class="field-input-empty mx-auto" style="opacity: 0;">
                        <div class="input-label medium-black-12px">再入力</div>
                        <input class="text-input-my pt-2 pl-3" type="password" modifier="font14" placeholder="パスワードを入力" v-model="password1" disabled>
                    </div>
                    <div class="button-div">
                        <v-ons-button @click="signup" class="bold-white-16px mx-auto button-long-primary-normal-my" :disabled="!isActive">次へ</v-ons-button>
                    </div>
                </div>
                </div>
        </div>
    </v-ons-page>
</template>

<script>

const extend = name => ({ name, extends: Template });

export default {
name: "login",
components: {
},
data() {
    return {
        name: "",
        password: "",
        password1: ""
    };
},
computed: {
    isActive(){
        return this.name!=""&&this.password!="";
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
    .x01 .textlabel-VMr6Om {
        background-color: transparent;
        height: auto;
        right: 2rem;
        letter-spacing: 0.00px;
        line-height: 18px;
        mix-blend-mode: normal;
        position: absolute;
        text-align: center;
        /* text-shadow: 0px 0px 20px #00000080; */
        top: 21rem;
        white-space: nowrap;
        width: auto;
    }   
</style>