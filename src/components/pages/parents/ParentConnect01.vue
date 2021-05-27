<template>
    <v-ons-page>
        <v-ons-card class="card-item">
            <v-ons-row style="margin: 5rem 0 3rem 0;">
                <v-ons-col width="10%">
                    <v-ons-back-button style="margin-top:-0.7rem">
                        <v-ons-icon modifier="outline" size="1.3rem" icon="ion-ios-menu, material:md-menu"></v-ons-icon>
                    </v-ons-back-button>
                </v-ons-col>
                <v-ons-col width="80%">
                    <div class="page-title txt-color-blue text-font-18">
                        <span>まず初めに、子どものアカウントと</span><br>
                        <span>連携しましょう</span>
                    </div>
                </v-ons-col>
            </v-ons-row>
            <v-ons-row style="display:table;">
                <v-ons-col class="img-col">
                    <img :src="parent.avatar_src" alt="" 
                            style="float:right; margin-right:-0.7rem" class="avatar-img">
                </v-ons-col>
                <v-ons-col class="img-col">
                    <div class="img-back">
                        <v-ons-row style="display:table;width:100%">
                            <v-ons-col style="display:table-cell;vertical-align:middle">
                                <div class="line-div"></div>
                            </v-ons-col>
                            <v-ons-col>
                                <div style="display:inline;">
                                    <img src="static/images/barcode.png" alt="" style="width: 5rem;">
                                </div>
                            </v-ons-col>
                            <v-ons-col style="display:table-cell;vertical-align:middle">
                                <div class="line-div"></div>
                            </v-ons-col>
                        </v-ons-row>
                    </div>
                </v-ons-col>
                <v-ons-col class="img-col">
                    <img :src="child.avatar_src" alt="" 
                        style="float: left;margin-left:-0.7rem" class="avatar-img">
                </v-ons-col>
            </v-ons-row>
            <div style="margin:2rem 1rem 1rem">
                <span class="page-content txt-color-black text-font-16">連携方法を選択</span>
            </div>
            <v-ons-button class="action-button"
                        @click="clicked_read_qr">
                <span class="text-font-16" style="width:100%;">QRコードを読み取って連携</span>
            </v-ons-button>
            <v-ons-button class="action-button"
                        @click="clicked_add_child">
                <span class="text-font-16" style="width:100%;">子どもを追加</span>
            </v-ons-button>
        </v-ons-card>
    </v-ons-page>
</template>

<script>
import ParentConnect02 from "./ParentConnect02"
export default {
    name: "parentconnect01",
    data: function(){
        return {
            parent: {"avatar_src":"static/images/lg_parent.jpg",},
            child: {"avatar_src":"static/images/lg_girl.png",},
        }
    },
    components: {
    },
    methods: {
        clicked_read_qr: function(){
            this.push_screen.push(ParentConnect02)
        },
        clicked_add_child: function(){

        },
    }
}
</script>

<style scoped>
    .card-item {
        position: absolute;
        left: 0;
        top: 0;
        width: 100%;
        height: 100%;
        margin: 0;
        padding: 0;
        border-radius: 0;
        background-color: white;
        display: table;
    }
    .page-title {
        font-family: "Noto Sans CJK JP";
        font-style: normal;
        font-weight: bold;
        line-height: 150%;
        text-align: center;
    }
    .page-content {
        font-family: "Noto Sans CJK JP";
        font-style: normal;
        font-weight: normal;
        line-height: 150%;
    }
    .txt-color-black {
        color: #303235;
    }
    .txt-color-blue {
        color: #0089FF;
    }
    .action-button {
        display: flex;
        width: 80%;
        left: 10%;
        text-align: center;
        margin: 1rem 0;
        padding: 0.7rem;
        border-radius:5rem;
        font-family: "Noto Sans CJK JP";
        font-weight: bold;
        color: white;
        background: #0089FF;
    }
    .img-back {
        margin: auto;
        width: fit-content;
        height: fit-content;
        padding: 4rem 0;
        border-radius: 50%;
        background: linear-gradient(to bottom, #04DBE9 , #29B9E7);
        display: table-cell;
        vertical-align: middle;
    }
    .avatar-img {
        border-radius:50%; 
        width:4rem;
        height:4rem;
    }
    .img-col {
        text-align: center;
        display:table-cell;
        align-content: center; 
        vertical-align: middle;
        padding: 0;
        margin: auto;
        width: 30%;
    }
    .line-div {
        display: block;
        width: 4rem;
        height: 0.2rem;
        background-color:white;
    }
</style>
