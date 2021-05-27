//Password
<template>
    <v-ons-page style="height: 100vh">
        <v-ons-toolbar class="setup-toolbar">
            <div class="left" style="width:35%">
                <v-ons-back-button>
                    <v-ons-icon modifier="outline" size="30px" icon="md-close, material:md-close-outline"></v-ons-icon>
                </v-ons-back-button>
            </div>
            <!-- </v-ons-col> -->
            <div class="center" style="width:30%">
                <p class="setup-toolbar-title text-font-18">パスワード変更</p>
            </div>
            <div class="right" style="width:35%">
                
            </div>
        </v-ons-toolbar>
        <v-ons-card class="card-item" style="margin-top: 2.9rem;text-align:left;">
            
            <div class="sub-title text-font-12" style="margin:3rem 0.5rem 0.3rem 0.5rem"><span>現在のパスワードを入力</span></div>
            <v-ons-input class="grey-btn" placeholder="半角英数字8文字以上"
                v-model="current_password" type="password" style="width: 100%;"
            >
            </v-ons-input>

            <div class="sub-title text-font-12" style="margin:3rem 0.5rem 0.3rem 0.5rem"><span>新しいパスワード</span></div>
            <v-ons-input class="grey-btn" :class="{'border-red': !is_correct_password}" placeholder="半角英数字8文字以上"
                v-model="new_password" type="password" style="width: 100%;"  @focus="focused_password"
            >
            </v-ons-input>
            
            <div class="alert-text text-font-12" style="margin:0.5rem 0.5rem;"
                    v-show="!is_correct_password"
            ><span>半角英数字8文字以上のパスワードにしてください</span></div>

            <div class="sub-title text-font-12" style="margin:3rem 0.5rem 0.3rem 0.5rem"><span>新しいパスワード（確認）</span></div>
            <v-ons-input class="grey-btn" placeholder="半角英数字8文字以上"
                v-model="confirm_password" style="width: 100%;" type="password"
            >
            </v-ons-input>
            <v-ons-button class="save-button" @click="clicked_save">
                <span class="text-font-16" style="width:100%;">保存</span>
            </v-ons-button>
        </v-ons-card>
    </v-ons-page>
</template>

<script>
export default {
    name: "setuppassword",
    data: function() {
        return {
            current_password: "",
            new_password: "",
            confirm_password: "",
            is_correct_password: true,
            is_confirmed_text_show: false,
        }
    },
    components: {
    },
    props: {
    },
    computed: {
    },
    methods: {
        validate: function() {
            var validRegex = /^(?=.*\d)(?=.*[a-zA-Z]).{8,20}$/;
            if(this.new_password!=""&&this.new_password.match(validRegex))
            {
                this.is_correct_password = true;
            }
            else{ this.is_correct_password = false; }
            var is_confirmed = this.new_password == this.confirm_password ? true:false;
            this.is_confirmed_text_show = !is_confirmed
            if(!is_confirmed)
            {
                // this.$ons.notification.toast('パスワードが異なります', { timeout: 1000, animation: 'fall' })
                this.$ons.notification.toast('パスワードが異なります', {
                    timeout: 153300,
                    modifier: 'failed thick',
                    animation: 'lift'
                });
            }
            if( this.is_correct_password && is_confirmed ) { return true; }
            else{ return false; }
        },
        clicked_save: function() {
            if( !this.validate() ) { return }

            // ////////   save act      ///////////////


        },
        focused_password: function() {
            this.is_correct_password = true;
        },
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
    .grey-btn{
        background: rgba(0, 0, 0, 0.05);
        border-radius: 6rem;
        padding: 0.7rem 1rem;
        margin-top: 0rem;
    }
    .left-list{
        font-family: "Noto Sans CJK JP";
        font-style: normal;
        font-weight: bold;
        line-height: 150%;
        color: #303235;
    }
    .center-list {
        margin-right: 2rem;
        text-align:right;
        display:grid;
        font-family: "Noto Sans CJK JP";
        font-style: normal;
        font-weight: normal;
        color: #193342;
    }
    .align-center {
        margin: auto;

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
    .mb-1 {
        margin-bottom: 1rem;
    }
    .col-center {
        text-align:center;
        margin:auto;
    }
    
    .text-font-13 {
        font-size: 13px;
        line-height: 16px;
    }
    .text-font-17 {
        font-size: 17px;
        line-height: 22px;
    }
    .sub-title {
        font-family: "Noto Sans CJK JP";
        font-style: normal;
        font-weight: bold;
        color: #193342;
    }
    .dialog-text {
        font-family: "SF Pro Display";
        font-style: normal;
        font-weight: normal;
        align-items: center;
        color: #303235;
    }
    .border-red {
        border-color: #EA3223;
        border-style: solid;
        border-width: thin;
        box-shadow: 0 0 5px #EA3223;
    }
    .alert-text {
        font-family: "Noto Sans CJK JP";
        font-style: normal;
        font-weight: normal;
        color: #EA3223;
        position: fixed;
    }
    .toast--failed {
        background: none !important;
        margin: 0 3rem 11rem 3rem !important;
    }
    .toast--failed__message {
        font-family: "Noto Sans CJK JP";
        font-style: normal;
        font-weight: normal;
        font-size: 1.2rem;
        line-height: 150%;
        text-align: center;
        color: #EA3223 !important;
    }
</style>