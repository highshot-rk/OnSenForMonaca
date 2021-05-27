<template>
    <v-ons-page>
        <div style="margin: 0; background: #ffffff">
            <div class="container-my" style="height: 95vh;">
                <div class="mx-auto">
                    <ons-toolbar class="practice-toolbar">
                        <div class="left" style="opacity: 0.6">
                            <ons-button @click="goToTeam" modifier="quiet">
                                <v-ons-icon size="1rem" icon="md-close, material:md-close"></v-ons-icon>
                            </ons-button>
                        </div>
                        <div class="center textlabel-my text-bold-black-18px"></div>
                        <div class="right w-2"></div>
                    </ons-toolbar>
                </div>
                <div class="x01 screen">
                    <div class="success-check" style="margin-top: 30vh">
                        <!-- <v-ons-icon icon="fa-check"></v-ons-icon> -->
                        <svg width="98" height="70" viewBox="0 0 98 70" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path d="M94.3334 4L32.0001 66.3333L3.66675 38" stroke="#0075FF" stroke-width="6.47619" stroke-linecap="round" stroke-linejoin="round"/>
                        </svg>
                        <div class="success-check-text">チームEを作成しました！</div>
                    </div>
                </div>
                </div>
        </div>
    </v-ons-page>
</template>

<script>

const extend = name => ({ name, extends: Template });
import TeamSetting from './TeamSetting.vue';

export default {
name: "success",
components: {
},
data() {
    return {
        
    };
},
computed: {
    
},
methods: {
    goToTeam() {
        this.push_screen.pop();
        while (this.push_screen.pop().name!=="TeamSetting"&&this.push_screen.length) {}
        this.push_screen.push(TeamSetting);
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
        margin: 0 0 0.5rem 0;
        padding: 3rem 0 0 0;
        text-align: center;
        align-items: center;
        border-radius: 0;
        background-color: white;
        border-bottom: solid 0px white;
        height: 88px;
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
</style>