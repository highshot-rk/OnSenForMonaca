<template>
    <v-ons-page>
        <div style="background-color: white; margin: auto">
            <div class="container-my" style="height: 95vh;">
                <div class="mx-auto">
                    <ons-toolbar class="practice-toolbar">
                        <div class="left" style="opacity: 0.6">
                            <ons-back-button>
                                <v-ons-icon size="1rem" icon="arrow-left, material:arrow-left"></v-ons-icon>
                            </ons-back-button>
                        </div>
                        <div class="center textlabel-my text-bold-black-18px">チームを新規作成</div>
                        <div class="right"></div>
                    </ons-toolbar>
                </div>
                <div class="x01 screen">
                    <div class="mt-5 field-input-empty mx-auto" style="margin-top: 6rem">
                        <div class="input-label medium-black-12px mb-1">チーム名</div>
                        <input class="text-input-my" type="text" modifier="font14" placeholder="例：A チーム" v-model="name" validated>
                    </div>
                    <div class="field-input-empty mx-auto">
                        <div class="input-label medium-black-12px mb-1">ホームプール（任意）</div>
                        <input class="text-input-my pt-2 pl-3" type="text" modifier="font14" placeholder="マイプール" v-model="homepool">
                    </div>
                    <div class="button-div" style="margin-top: 10rem">
                        <v-ons-button @click="save" class="bold-white-16px mx-auto button-long-primary-normal-my" :disabled="!isActive">次へ</v-ons-button>
                    </div>
                </div>
                </div>
        </div>
    </v-ons-page>
</template>

<script>

const extend = name => ({ name, extends: Template });
import Success from './Success.vue';

export default {
name: "createteam",
components: {
},
data() {
    return {
        name: "",
        homepool: "",
    };
},
computed: {
    isActive(){
        return this.name!=""&&this.homepool!="";
    }
},
methods: {
    save(){
        this.push_screen.push(Success);
    }
},
created() {
        
},
}
</script>

<style scoped>
    
    /* @import './css/styleguide.css';  */
    
    span.back-button__icon{
        display: none !important;
    }
</style>