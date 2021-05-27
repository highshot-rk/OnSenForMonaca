<template>
  <v-ons-page>
    <div>
      <!-- <div class="header">
        <v-ons-back-button modifier="quiet">
          <v-ons-icon size="1rem" icon="arrow-left, material:arrow-left"></v-ons-icon>
        </v-ons-back-button>
        <span class="h_title">プロフィールを設定して始める</span>
      </div> -->
      <img src="/static/images/childsuccessback.png" style="position: absolute; top: 1rem; left: 0; z-index: 0; width: 100%; height: 600px">
      <v-ons-card class="card-item" style="margin-top: 2.9rem; padding-top: 0.2rem">
        <div class="photo mt-5" style="margin-top: 10rem">
          <div>
            <div class="p_img">
              <img :src="photo_url" style="z-index: 1" onerror="this.src='static/images/no_user.png'"/>
            </div>
            <div class="p_t_btn">
              ひまりさんと<br><span style="color: #0089FF">連携しました！</span>
            </div>
          </div>
          <div class="b_btn"><v-ons-button class="b_btn_bt"><span class="b_btn_cap">サマリーを確認</span></v-ons-button></div>
        </div>
      </v-ons-card>
    </div>
  </v-ons-page>
</template>

<script>
import Camera from "./Camera";

export default {
    name: "childphotosuccess",
    data() {
      return {
        photo_url: 'static/images/no_user.png',
        actionSheetVisible: false,
        full_name: '',
        isSaved: false,
        isLinked: false,
        wantOut: false,
        deleteDialogVisible: false,
      }
    },
    methods: {
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
      },
      save() {
        this.isSaved = true;
      },
      link() {
        this.isLinked = true;
      },
      codeCopy() {
        return
      },
      deleteMember() {
        this.isSaved = false;
        this.isLinked = false;
        this.deleteDialogVisible = false;
        this.$ons.notification.toast('選手を削除しました', {timeout: 2000, modifier: 'my-toast-higher'});
      }
    }

}
</script>

<style scoped>
  .blue{
    color: #007AFF;
  }
  .m_title{
    font-family: Noto Sans JP;
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
      font-family: Noto Sans CJK JP;
      font-style: normal;
      font-weight: bold;
      font-size: 16px;
      line-height: 150%;
      color: #FFFFFF;
  }
  .b_btn{
    margin-top: 17rem;
    display: flex;
    position: absolute;
    top: 50%;
    left: calc(50vw - 160px);
    justify-content: center;
  }
  .b_btn_bt{
    width: 320px;
    padding: 16px 96px;
    background: #0089FF;
    border-radius: 30px;
  }
  .b_btn_bt_link{
    width: 320px;
    padding: 14px 36px;
    background: #29B9E7;
    border-radius: 30px;
  }
  .b_title{
    margin-top: 115px;
    margin-left: 33px;
    margin-right: 33px;
    font-family: Noto Sans CJK JP;
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
    font-family: Noto Sans CJK JP-medium;
    font-style: normal;
    font-weight: normal;
    font-size: 12px;
    line-height: 150%;
    color: #000000;
  }
  .f_title>span{
    width: 72px;
    font-family: Noto Sans CJK JP;
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
    font-family: Noto Sans CJK JP;
    font-style: normal;
    font-weight: normal;
    font-size: 12px;
    line-height: 150%;
    color: #000000;
  }
  .p_t_btn{
    /* display: flex; */
    justify-content: center;
    font-family: Noto Sans CJK JP;
    font-style: normal;
    font-weight: bold;
    font-size: 20px;
    line-height: 150%;
    /* or 30px */
    margin-top: 2rem;
    text-align: center;

    /* Neutral / Black */

    color: #303235;
  }
  .p_btn{
    width: 160px;
    height: 36px;
    border: 1px solid #0089FF;
    border-radius: 30px;
    margin-top: 16px;
    display: flex;
    justify-content: center;
    font-family: Noto Sans CJK JP;
    font-style: normal;
    font-weight: bold;
    font-size: 16px;
    line-height: 150%;
    text-align: center;
    color: #0089FF;
  }
  .p_btn>span{
    font-family: Noto Sans CJK JP;
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
    /* margin-top: 20px; */
    font-family: Noto Sans CJK JP-medium;
    font-style: normal;
    font-weight: normal;
    font-size: 12px;
    line-height: 150%;
    color: #303235;
  }
  .p_title>span{
    margin-left: 28px;
      font-family: Noto Sans CJK JP;
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
  .practice-toolbar {
    margin: 0 0 0.5rem 0;
    padding: 3rem 0 0 0;
    text-align: center;
    align-items: center;
    border-radius: 0;
    background-color: white;
    border-bottom: solid 3px #EEEEEE55;
    height: 88px;
  }
  .toolbar-title {
    font-family: Noto Sans JP;
    font-style: normal;
    font-weight: bold;
    font-size: 18px;
    color: #303235;
    margin-bottom: 0;
    height: 2.5rem;
  }
  .toolbar-sub-title {
    font-family: SF Pro Display;
    font-style: normal;
    font-weight: normal;
    font-size: 11px;
    line-height: 13px;
    text-align: center;
    margin-top: 0;
    height: 2rem;
  }
  .photo{
    margin-top: 3rem;
  }
  .card-item {
    margin: 0.2rem 0 0 0;
    width: 100%;
    padding: 0.5rem;
    border-radius: 0.1rem;
    height: calc(100vh - 2.9rem);
    overflow: auto;
  }
  .p_bottom{
    font-family: Noto Sans JP;
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 150%;
    color: #EA3223;
    text-align: center;
    margin-top: 1rem;
    /* margin-bottom: 2rem; */
  }
  .btn_link{
    /* position: absolute; */
    /* top: 57%; */
    /* left: 7.5%; */
    text-align: center;
    margin: auto;
  }
  .linked-text{
    font-family: SF Pro Text;
    font-style: normal;
    font-weight: normal;
    font-size: 12px;
    line-height: 150%;
    color: #5496D7;
    width: fit-content;
    margin: auto;
    margin-top: 1rem;
  }
  .delete-button{
    font-family: SF Pro Text;
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    /* identical to box height, or 24px */
    text-align: center;
    /* Primary / Red */
    color: #EA3223;
  }
  .tab-bottom {
    display: flex;
    justify-content: space-around;
    background-color: white;
    /* border-top: 1px solid lightgray; */
    /* border-top-left-radius: 0.5rem; */
    /* border-top-right-radius: 0.5rem; */
    margin-top: 10rem !important
    /* height: 10rem; */
  }
  .tool_bottom{
    background-color: white;
    /* height: 10rem; */
    padding: 0;
    box-shadow: none;
  }
  .line-text{
    font-family: SF Pro Display;
    font-style: normal;
    font-weight: normal;
    font-size: 12px;
    line-height: 150%;
    align-items: center;
    color: #8293A3;
  }
</style>
