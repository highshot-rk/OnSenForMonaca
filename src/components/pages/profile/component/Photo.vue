<template>
  <v-ons-page>
    <div>
      <div class="header">
        <v-ons-button modifier="quiet"><span class="material-icons h_left" @click="back">west</span></v-ons-button>
        <span class="h_title">プロフィールを設定して始める</span>
      </div>
      <div class="photo">
        <div class="p_title"><span>プロフィール写真 </span></div>
        <div>
          <div class="p_img">
            <img :src="photo_url" oneeror="this.src='static/images/no_user.png'"/>
          </div>
          <div class="p_t_btn">
            <v-ons-button modifier="outline" class="p_btn" @click="actionSheetVisible = true"><span>写真を設定</span></v-ons-button>
          </div>
        </div>
      </div>
      <div class="info">
        <div class="name_1"><span >氏名</span></div>
        <div class="name">
          <v-ons-input placeholder="姓" class="grey_btn" v-model="first_name"></v-ons-input>
          <v-ons-input placeholder="名" class="grey_btn" v-model="last_name"></v-ons-input>
        </div>
        <div class="full_name">
          <div class="f_title"><span>ニックネーム</span></div>
          <div class="f_input"><v-ons-input placeholder="ユーザーネームを入力" class="grey_btn with_327" v-model="full_name"></v-ons-input></div>
        </div>
      </div>
      <div class="bottom">
        <div class="b_title"><span>※登録された写真とユーザーネームを元に、コーチが練習メニューを組んだり、練習時の並び替えを行います。
本人だとわかるような写真と名前にしましょう。</span></div>
        <div class="b_btn"><v-ons-button class="b_btn_bt"><span class="b_btn_cap">保存</span></v-ons-button></div>
      </div>
      <div>
        <v-ons-action-sheet
              :visible.sync="actionSheetVisible"
              cancelable
              title="<span style='font-family: 'Noto Sans JP';
    font-style: normal;
    font-weight: bold;
    font-size: 16px;
    line-height: 150%;
    text-align: center;
    color: #303235;'>写真を設定</span>"
            >
              <v-ons-action-sheet-button icon="md-square-o" @click="show_got_data"><span>カメラローるから選ぶ</span></v-ons-action-sheet-button>
              <v-ons-action-sheet-button icon="md-square-o" modifier="destructive" @click="show_camera"><span class="blue">カメラを起動</span></v-ons-action-sheet-button>
              <v-ons-action-sheet-button icon="md-square-o" @click="close_modal"><span>キャンセル</span></v-ons-action-sheet-button>
            </v-ons-action-sheet>
      </div>
    </div>
  </v-ons-page>
</template>

<script>
import Camera from "./Camera";

export default {
    name: "photo",
    data() {
      return {
        photo_url: 'static/images/no_user.png',
        first_name: '',
        last_name: '',
        full_name: '',
        actionSheetVisible: false
      }
    },
    methods: {
      back(){
        this.push_screen.pop();
      },
      show_camera(){
        this.push_screen.push(Camera);
        this.actionSheetVisible = false;
        //this.$emit('push-page', Camera);
      },
      show_got_data(){
        this.first_name = '佐藤';
        this.last_name = 'ひまり';
        this.full_name = 'ひまり';
        this.photo_url = 'static/images/girl.png';
      },
      close_modal(){
        this.actionSheetVisible = false;
      }
    }

}
</script>

<style scoped>
  .blue{
    color: #007AFF;
  }
  .m_title{
    font-family: "Noto Sans JP";
    font-style: normal;
    font-weight: bold;
    font-size: 16px;
    line-height: 150%;
    text-align: center;
    color: #303235;
  }
  .b_btn_cap{
      letter-spacing: 0.00px;
      line-height: 24px;
      mix-blend-mode: normal;
      text-align: center;
      white-space: nowrap;
      width: auto;
      justify-content: center;
      display: flex;
      position: static;
      font-family: "Noto Sans CJK JP";
      font-style: normal;
      font-weight: bold;
      font-size: 16px;
      line-height: 150%;
      color: #FFFFFF;
  }
  .b_btn{
    margin-top: 48px;
    display: flex;
    justify-content: center;
  }
  .b_btn_bt{
    width: 84.5vw;
    padding: 16px 96px;
    background: #0089FF;
    border-radius: 30px;
  }
  .b_title{
    margin-top: 115px;
    margin-left: 33px;
    margin-right: 33px;
    font-family: "Noto Sans CJK JP";
    font-style: normal;
    font-weight: normal;
    font-size: 12px;
    line-height: 150%;
    color: #303235;
    width: 313px;
    display: flex;
    justify-content: center;
  }
  .f_input{
    margin-top: 8px;
    display: flex;
    justify-content: center;
  }
  .f_title{
    margin-top: 16px;
    margin-left: 24px;
  }
  .f_title>span{
    width: 72px;
    font-family: "Noto Sans CJK JP";
    font-style: normal;
    font-weight: normal;
    font-size: 12px;
    line-height: 150%;
  }
  .with_327{
    width: 307px !important;
    padding: 8px 15px;
  }
  .name{
    display: flex;
    justify-content: space-evenly;
    margin-top: 8px;
  }
  .grey_btn{
    width: 135px;
    background: rgba(0, 0, 0, 0.05);
    border-radius: 34px;
    padding: 8px 15px;
  }
  .name_1{
    margin-top: 38px;
    margin-left: 24px;
    font-family: "Noto Sans CJK JP";
    font-style: normal;
    font-weight: normal;
    font-size: 12px;
    line-height: 150%;
    color: #000000;
  }
  .p_t_btn{
    display: flex;
    justify-content: center;
  }
  .p_btn{
    width: 160px;
    height: 36px;
    border: 1px solid #0089FF;
    border-radius: 30px;
    margin-top: 16px;
    display: flex;
    justify-content: center;
  }
  .p_btn>span{
    font-family: "Noto Sans CJK JP";
    font-style: normal;
    font-weight: bold;
    font-size: 16px;
    line-height: 150%;
    text-align: center;
    color: #0089FF;
    flex: none;
    order: 0;
    flex-grow: 0;
    margin: 0px 10px;
    background-color: transparent;
    height: auto;
    letter-spacing: 0.00px;
    line-height: 24px;
    mix-blend-mode: normal;
    position: absolute;
    text-align: center;
    top: 6px;
    white-space: nowrap;
    width: auto;
  }
  .p_img{
    display: flex;
    justify-content: center;
    margin-top: 16px;
  }
  .p_img>img{
    width: 120px;
    height: 120px;
    border-radius: 50%;
  }
  .p_title{
    margin-top: 20px;
  }
  .p_title>span{
    margin-left: 28px;
      font-family: "Noto Sans CJK JP";
      font-style: normal;
      font-weight: normal;
      font-size: 12px;
      line-height: 150%;
      color: #303235;
  }
  .header{
    border-bottom: 1px solid lightgrey;
  }
  .h_left{
    margin-left: 5px;
    margin-top: 48px;
    color: #303235;
  }
  .h_title{
    margin-top: 53px;
    margin-left: 20px;
    background-color: transparent;
    mix-blend-mode: normal;
    position: absolute;
    white-space: nowrap;
    color: var(--mine-shaft);
    font-family: var(--font-family-noto_sans_cjk_jp-bold);
    font-size: var(--font-size-xxxxl);
    font-style: normal;
    font-weight: 700;
  }


</style>
