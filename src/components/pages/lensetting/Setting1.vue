<template>
    <v-ons-page>
        <div style="margin: 0; background: #ffffff;overflow: hidden;height: 100vh;">
            <div class="container-center-horizontal">
                <div class="x01 screen">
                    <v-ons-toolbar class="practice-toolbar">
                        <div class="left" style="opacity: 0.6">
                            <v-ons-back-button>
                                <v-ons-icon size="1rem" icon="arrow-left, material:arrow-left"></v-ons-icon>
                            </v-ons-back-button>
                        </div>
                        <div class="center">
                            <span class="toolbar-title textlabel-my text-bold-black-18px">レーン設定</span>
                        </div>
                        <div class="right" style="opacity: 0.6">
                            <v-ons-button modifier="quiet" class="setting-right-next-len">
                                次へ
                            </v-ons-button>
                        </div>
                    </v-ons-toolbar>
                    <div class="container-my" style="margin-top: 5.5rem; overflow-y: auto;height: 86vh">
                        <div class="setting-number">
                            <span class="setting-number-span">レーン数</span>
                            <span class="float-right-my">
                                <v-ons-button class="right-next-circle"><div class="right-next-circle-text"><v-ons-icon icon="fa-minus"></v-ons-icon></div></v-ons-button>
                                <span style="margin: 0 16px">1</span>
                                <v-ons-button class="right-next-circle"><div class="right-next-circle-text"><v-ons-icon icon="fa-plus"></v-ons-icon></div></v-ons-button>
                            </span>
                        </div>
                        <div class="setting-number mb-2">
                            <span class="setting-number-span">出席リスト（名簿）</span>
                            <span class="float-right-my" style="margin: -9px">
                                <v-ons-button modifier="quiet" class="setting-number-span right-next-12">
                                    <span style="padding-right: 1rem">12名 <v-ons-icon icon="fa-chevron-right" style="padding-left: 1rem"></v-ons-icon></span>
                                </v-ons-button>
                            </span>
                        </div>
                        <div class="">
                            <v-ons-row>
                                <v-ons-col v-for="n in data.type" :key="n" :width="100/data.type+'%'">
                                <div :style="n<data.type?'margin-right: 4px;':''+n>1?'margin-left: 4px;':''">
                                    <div  v-if="data.type!==1" :class="'setting-les'+n">レーン{{n}}</div>
                                    <div>
                                        <v-ons-row>
                                            <v-ons-col :width="data.type===1?'50%':'100%'"  class="mb-2">
                                                <v-ons-row>
                                                    <v-ons-col v-if="data.type!==3" width="30%">
                                                        <div class="text-input--font14 mt-2 label-my">人数</div>
                                                    </v-ons-col>
                                                    <v-ons-col>
                                                        <div class="">
                                                            <v-ons-select v-model="selectedItem[n-1]" class="select-my">
                                                                <option v-for="(item, index) in items" :value="item.value" :key="index">
                                                                {{ item.text }}
                                                                </option>
                                                            </v-ons-select>
                                                        </div>
                                                    </v-ons-col>
                                                </v-ons-row>
                                            </v-ons-col>
                                            <v-ons-col :width="data.type===1?'50%':'100%'"  class="mb-2">
                                                <v-ons-row class="">
                                                    <v-ons-col v-if="data.type===1" width="4%">
                                                    </v-ons-col>
                                                    <v-ons-col v-if="data.type!==3" width="30%">
                                                        <div class="text-input--font14 mt-2 label-my">選手間</div>
                                                    </v-ons-col>
                                                    <v-ons-col>
                                                        <div class="">
                                                            <v-ons-select v-model="selectedItem1[n-1]" class="select-my">
                                                                <option v-for="(item, index) in items1" :value="item.value" :key="index">
                                                                    {{ item.text }}
                                                                </option>
                                                            </v-ons-select>
                                                        </div>
                                                    </v-ons-col>
                                                </v-ons-row>
                                            </v-ons-col>
                                        </v-ons-row>
                                    </div>
                                    <div>
                                        <div v-for="(item, index) in participating_players_list" :key="index" :class="'block'+n+' mb-1'">
                                            <v-ons-row>
                                                <v-ons-col style="display: flex;">
                                                    <span class="mt-1 mr-2 ml-0">#{{index+1}}</span>
                                                    <img v-if="data.type<3" :src="item.avatar_src" :alt="item.avatar_src" width="32rem" height="32rem" class="avatar-md">
                                                    <v-ons-list v-if="data.type===1" style="background: none">
                                                        <v-ons-list-item expandable :expanded.sync="isExpanded.slice()[index]" modifier="nodivider" style="margin-top: -8px; width: fit-content">
                                                            {{item.name}}
                                                            <div class="expandable-content">Expandable content</div>
                                                        </v-ons-list-item>
                                                    </v-ons-list>
                                                    <p style="position: absolute; top: .8rem; right: .5rem;">
                                                        <svg width="10" height="16" viewBox="0 0 10 16" fill="none" style="fload:right">
                                                            <path d="M4 14C4 15.1 3.1 16 2 16C0.9 16 0 15.1 0 14C0 12.9 0.9 12 2 12C3.1 12 4 12.9 4 14ZM2 6C0.9 6 0 6.9 0 8C0 9.1 0.9 10 2 10C3.1 10 4 9.1 4 8C4 6.9 3.1 6 2 6ZM2 0C0.9 0 0 0.9 0 2C0 3.1 0.9 4 2 4C3.1 4 4 3.1 4 2C4 0.9 3.1 0 2 0ZM8 4C9.1 4 10 3.1 10 2C10 0.9 9.1 0 8 0C6.9 0 6 0.9 6 2C6 3.1 6.9 4 8 4ZM8 6C6.9 6 6 6.9 6 8C6 9.1 6.9 10 8 10C9.1 10 10 9.1 10 8C10 6.9 9.1 6 8 6ZM8 12C6.9 12 6 12.9 6 14C6 15.1 6.9 16 8 16C9.1 16 10 15.1 10 14C10 12.9 9.1 12 8 12Z" fill="#D3D3D3"/>
                                                        </svg>
                                                    </p>
                                                </v-ons-col>
                                            </v-ons-row>
                                            <img v-if="data.type===3" :src="item.avatar_src" :alt="item.avatar_src" width="32rem" height="32rem" class="avatar-md mt-1">
                                            <v-ons-list v-if="data.type!==1" style="background: none;" :style="data.type===2?'margin-left: 2.2rem':''" class="mt-1">
                                                <v-ons-list-item expandable :expanded.sync="isExpanded.slice()[index]" modifier="nodivider" style="margin-top: -8px; width: fit-content; font-family: 'SF Pro Text'; padding-left: 0">
                                                    {{item.name}}
                                                    <div class="expandable-content">Expandable content</div>
                                                </v-ons-list-item>
                                            </v-ons-list>
                                            <p class="small-opacity-my" :style="data.type===2?'margin-left: 2.2rem':''">10秒</p>
                                        </div>
                                    </div>
                                </div>
                                </v-ons-col>
                            </v-ons-row>
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
name: "setting",
components: {
},
data() {
    return {
        items: [
            { text: '4名', value: '4名' },
            { text: '8名', value: '8名' },
            { text: '12名', value: '12名' }
        ],
        selectedItem: ['4名', '4名', '4名'],
        items1: [
            { text: '10秒', value: '10秒' },
            { text: '12秒', value: '12秒' },
            { text: '16秒', value: '16秒' }
        ],
        selectedItem1: ['10秒' ,'10秒', '10秒'],
        isExpanded: [false, false, false, false],
    };
},
props: {
        "participating_players_list": {
            type: Array,
            default: ()=>[
                {"name":"吉田 花子", "avatar_src":"static/images/swimmer/swimmer01.jpg"},
                {"name":"斎藤 優子", "avatar_src":"static/images/swimmer/swimmer02.jpg"},
                {"name":"村田 隆", "avatar_src":"static/images/swimmer/swimmer03.jpg"},
                {"name":"吉岡 太朗", "avatar_src":"static/images/swimmer/swimmer04.jpg"},
                // {"name":"宮下優子", "avatar_src":"static/images/swimmer/swimmer05.jpg"},
                // {"name":"佐藤義行", "avatar_src":"static/images/swimmer/swimmer06.jpg"},
                // {"name":"村上晴之助", "avatar_src":"static/images/swimmer/swimmer07.jpg"},
                // {"name":"鈴木竜也", "avatar_src":"static/images/swimmer/swimmer08.jpg"},
                // {"name":"池江璃花子", "avatar_src":"static/images/swimmer/swimmer09.jpg"},
                // {"name":"吉田 花子", "avatar_src":"static/images/swimmer/swimmer01.jpg"},
                // {"name":"斎藤 優子", "avatar_src":"static/images/swimmer/swimmer02.jpg"},
                // {"name":"村田 隆", "avatar_src":"static/images/swimmer/swimmer03.jpg"},
                // {"name":"吉岡 太朗", "avatar_src":"static/images/swimmer/swimmer04.jpg"},
                // {"name":"宮下優子", "avatar_src":"static/images/swimmer/swimmer05.jpg"},
                // {"name":"佐藤義行", "avatar_src":"static/images/swimmer/swimmer06.jpg"},
                // {"name":"村上晴之助", "avatar_src":"static/images/swimmer/swimmer07.jpg"},
                // {"name":"鈴木竜也", "avatar_src":"static/images/swimmer/swimmer08.jpg"},
                // {"name":"池江璃花子", "avatar_src":"static/images/swimmer/swimmer09.jpg"},
            ]
        },
    },
computed: {
    isActive(){
        return this.name!=""&&this.password!=""&&this.password==this.password1;
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
    span.back-button__icon{
        display: none !important;
    }
    .setting-les1{
        font-family: "SF Pro Display";
        font-style: normal;
        font-weight: normal;
        font-size: 16px;
        line-height: 150%;
        margin-bottom: 14px;
        align-items: center;
        text-align: center;
        color: #29B9E7;
    }
    .setting-les2{
        font-family: "SF Pro Display";
        font-style: normal;
        font-weight: normal;
        font-size: 16px;
        line-height: 150%;
        margin-bottom: 14px;
        align-items: center;
        text-align: center;
        color: #E99B04;
    }
    .setting-les3{
        font-family: "SF Pro Display";
        font-style: normal;
        font-weight: normal;
        font-size: 16px;
        line-height: 150%;
        margin-bottom: 14px;
        align-items: center;
        text-align: center;
        color: #E45A8C;
    }
    div.block1 {
        padding: 10px;
        border: 2px solid #29B9E7;
        border-radius: 8px;
        position: relative;
    }
    div.block2 {
        padding: 10px;
        border: 2px solid #E99B04;
        border-radius: 8px;
        position: relative;
    }
    div.block3 {
        padding: 10px;
        border: 2px solid #E45A8C;
        border-radius: 8px;
        position: relative;
    }
    .avatar-md {
        border-radius: 50%;
    }
    .small-opacity-my{
        font-family: "SF Pro Text";
        font-style: normal;
        font-weight: normal;
        font-size: 12px;
        line-height: 150%;
        color: #8293A3;
    }
    .practice-toolbar {
        margin: 0 0 0rem 0;
        padding: 3rem 0 0 0;
        text-align: center;
        align-items: center;
        border-radius: 0;
        background-color: white;
        /* height: 88px; */
        border-bottom: solid 1px lightgrey;
    }
    .right-next-circle{
        /* background: #0089FF; */
        position: relative;
        /* display: block; */
        border-radius: 50%;
        border: none;
        text-align: center;
        padding: 0;
        /* padding: 0 12px; */
        width: 20px;
        height: 20px;
        /* margin: 0 16px; */
        color: white;
        font-size: 10px;
        /* font-weight: bold; */
    }
    .right-next-circle-text{
        position: absolute;
        top: -6px;
        left: 5.5px;
    }
</style>