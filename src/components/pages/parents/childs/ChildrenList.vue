//子ども一覧
<template>
    <v-ons-page style="height: 100vh">
        <v-ons-toolbar class="setup-toolbar">
            <div class="left" style="width:35%">
                <v-ons-back-button>
                    <v-ons-icon modifier="outline" size="1.5rem" icon="md-arrow-left, material:md-arrow-left-outline"></v-ons-icon>
                </v-ons-back-button>
            </div>
            <!-- </v-ons-col> -->
            
            <div class="center" style="width:30%">
                <p class="setup-toolbar-title text-font-18">子ども一覧</p>
            </div>
            <div class="right" style="width:35%">
                
            </div>
        </v-ons-toolbar>
        <v-ons-card class="card-item" style="margin-top: 2.9rem; margin-bottom: 0;">
            <v-ons-list>
                <v-ons-list-item v-for="(child, index) in child_list" :key="index"
                    tappable modifier="chevron" @click="gotoChildDetailPage">
                    <div class="left">
                        <img :src="child.avatar_src" alt="" width="32rem" height="32rem" class="avatar-md">
                    </div>
                    <div class="center list-text text-font-16 txt-color-black" style="padding: 1.2rem 0.8rem;">
                        <span>{{child.name}}</span>
                    </div>
                    <div class="right list-text text-font-12 txt-color-gray">
                        <span>アカウント譲渡済み</span>
                    </div>
                </v-ons-list-item>
            </v-ons-list>
            <v-ons-button modifier="quiet" style="float:left; margin-top:1rem;" class="list-text txt-color-blue text-font-16"
            >
                <span style="padding: 1rem;">
                    <v-ons-icon icon="md-plus, material:md-plus-outline"
                                size="1rem" style="height: 0.2rem;"
                    >
                    </v-ons-icon>
                </span>
                <span>新規種類の追加</span>
            </v-ons-button>
        </v-ons-card>
    </v-ons-page>
</template>

<script>
export default {
    name: "childrenlist",
    data: function() {
        return {
            child_list: [
                {"name":"ひまり","avatar_src":"static/images/swimmer/swimmer02.jpg",},
                {"name":"ひなこ","avatar_src":"static/images/swimmer/swimmer03.jpg"},
                {"name":"宮下優子", "avatar_src":"static/images/swimmer/swimmer05.jpg"},
                {"name":"佐藤義行", "avatar_src":"static/images/swimmer/swimmer06.jpg"},
                {"name":"村上晴之助", "avatar_src":"static/images/swimmer/swimmer07.jpg"},
                {"name":"鈴木竜也", "avatar_src":"static/images/swimmer/swimmer08.jpg"},
                {"name":"池江璃花子", "avatar_src":"static/images/swimmer/swimmer09.jpg"},
                {"name":"吉田 花子", "avatar_src":"static/images/swimmer/swimmer04.jpg"},
            ],
        }
    },
    components: {
    },
    props: {
    },
    computed: {
    },
    methods: {
        addChild: function () {
            // this.addLevelDialogVisible = false;
        },
        gotoChildDetailPage: function(){

        }
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
    .tool-button {
        /* margin-left: 1rem; */
        text-align: right;
        padding: 0;
        float: right;

    }
    .left-list{
        font-family: "Noto Sans CJK JP";
        font-style: normal;
        font-weight: bold;
        line-height: 150%;
        color: #303235;
    }
    .align-center {
        margin: auto;

    }
    .list-text {
        font-family: "Noto Sans JP";
        font-style: normal;
        font-weight: normal;
        line-height: 150%;
    }

    .avatar-md {
        border-radius: 50%;
    }
    .txt-color-black {
        color: #303235;
    }
    .txt-color-blue {
        color: #0089FF;
    }
    .txt-color-gray {
        color: #707070;
    }
</style>