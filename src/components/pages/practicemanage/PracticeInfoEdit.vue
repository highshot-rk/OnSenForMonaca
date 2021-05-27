
<template>
    <v-ons-page style="height: 100vh">
        <v-ons-toolbar class="practice-toolbar">
            <div class="left" style="width:35%">
                <v-ons-back-button>
                    <v-ons-icon modifier="outline" size="30px" icon="md-close, material:md-close-outline"></v-ons-icon>
                </v-ons-back-button>
            </div>
            <!-- </v-ons-col> -->
            <div class="center" style="width:30%">
                <p class="practice-toolbar-title text-font-18">練習情報の編集</p>
            </div>
            <div class="right" style="width:35%">
                
            </div>
        </v-ons-toolbar>
        <v-ons-card class="card-item" style="margin-top: 2.9rem; margin-bottom: 0;">
            <div class="ac-title text-font-12"><span>練習開始日時</span></div>
            <v-ons-row>
                <v-ons-col width="50%">
                    <v-ons-input class="grey_btn" type="date" min='2000/11/23' v-model="practice_start_date" style="width:90%; float:left;"></v-ons-input>
                </v-ons-col>
                
                <v-ons-col width="50%">
                    <v-ons-select class="grey_btn" style="width: 90%; float:right;"
                        v-model="practice_start_time"
                    >
                    </v-ons-select>
                </v-ons-col>
            </v-ons-row>
            <div class="ac-title text-font-12"><span>プール</span></div>
            <v-ons-input class="grey_btn" placeholder="ロンド成増" v-model="swimming_pool"
                    style="display: flex; justify-content: center; text-align: center;"
                    pattern="YYYY-MM-DD"
            ></v-ons-input>
            <v-ons-button class="save-button text-font-16"
                    @click="saveClick"
            >
                <span style="width:100%;">保存</span>
            </v-ons-button>
        </v-ons-card>
    </v-ons-page>
</template>

<script>
export default {
    name: "practiceinfoedit",
    data: function() {
        return {
            practice_start_time: "7:30",
            practice_start_date: "2021-05-24",
            swimming_pool: "ロンド成増",
        }
    },
    components: {
    },
    props: {
    },
    computed: {
    },
    methods: {
        saveClick: function(){
            console.log(this.practice_start_date)
        }
    },
    
}
</script>

<style scoped>
    .practice-toolbar {
        margin: 0 0 0.5rem 0;
        padding: 3rem 0 0 0;
        text-align: center;
        align-items: center;
        border-radius: 0;
        background-color: white;
        height: 5.4rem;
    }
    .practice-toolbar-title {
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
    .grey_btn{
        background: rgba(0, 0, 0, 0.05);
        border-radius: 6rem;
        padding: 0.4rem 1rem;
        margin: 0.2rem 0.5rem 0.5rem 0.5rem;
    }
    .add_content{
        margin-top:70px;
    }
    .ac-title{
        font-family: "Noto Sans CJK JP";
        font-style: normal;
        font-weight: bold;
        font-size: 12px;
        text-align: left;
        color: #193342;
        margin: 0.6rem 0 0.5rem 0;
    }
    .save-button {
        position:fixed;
        display: flex;
        bottom: 11vh;
        width: 90%;
        text-align: center;
        margin: auto;
        padding: 0.8rem;
        border-radius:5rem;
        font-family: "Noto Sans CJK JP";
        font-weight: bold;
    }
</style>