<template>
  <v-ons-page>
    <v-ons-toolbar class="header">
        <div class="left"><v-ons-back-button modifier="quiet" class=" h_left"><span class="material-icons">west</span></v-ons-back-button></div>
        <div class="center"><span class="h_title">家族設定</span></div>
    </v-ons-toolbar>
    <div class="family_list">
      <v-ons-list>
        <v-ons-list-item class="lst_title">家族一覧</v-ons-list-item>
        <div v-if="registered_family.length == 0" class="no_family">
          <span>家族は登録されていません</span>
        </div>
        <v-ons-list-item v-for="item in registered_family" :key="item">
          <span class="left lst_content_left">{{item}}</span>
          <v-ons-button modifier="quiet" class="right lst_content_right"  @click="deletefamily"><span>つながりを解除</span></v-ons-button>
        </v-ons-list-item>
      </v-ons-list>
    </div>
    <div class="addBtn">
      <v-ons-button modifier="quiet" class=" abt_top-32" @click="addFamily"><span class="material-icons ml-30">add</span><span class="ml-21">家族を招待する</span></v-ons-button>
    </div>
    <v-ons-bottom-toolbar class="tool_bottom">
      <div class="tab-bottom">
        <div style="text-align: center">
          <v-ons-button modifier="quiet">
          <span style="width: 18px; height: 18px; margin: 3px;" class='material-icons'>event_note</span>
          <p style="margin: -10px; font-weight: bold;font-size: 10px;">サマリー</p>
          </v-ons-button>
        </div>
        <div style="text-align: center">
          <v-ons-button modifier="quiet" style="color:#8293A3;">
            <span style="width: 18px; height: 18px; margin: 3px;" class='material-icons'>menu_book</span>
            <p style="margin: -10px; font-weight: bold; font-size: 10px;">スイムノート</p>
          </v-ons-button>
        </div>
      </div>
    </v-ons-bottom-toolbar>
    <v-ons-action-sheet
      :visible.sync="inviteMethodFlag"
      cancelable
      title="招待方法を選択"
      style="text-align: left;font-family: 'Noto Sans CJK JP';
              font-style: normal;
              font-weight: normal;
              font-size: 16px;
              line-height: 150%;
              color: #303235;"
    >
      <v-ons-row class="white mt-10">
        <v-ons-col width="20%">
        </v-ons-col>
        <v-ons-col width="20%">
          <v-ons-button modifier="quiet">
            <img src="/static/images/line.png" alt="" class="social"/>
          </v-ons-button>
        </v-ons-col>
        <v-ons-col width="20%">
          <v-ons-button modifier="quiet">
            <img src="/static/images/qr.png" alt="" class="social"/>
          </v-ons-button>
        </v-ons-col>
        <v-ons-col width="20%">
          <v-ons-button modifier="quiet">
            <img src="/static/images/copy.png" alt="" class="social"/>
          </v-ons-button>
        </v-ons-col>
        <v-ons-col width="20%">
        </v-ons-col>
      </v-ons-row>
      <v-ons-row class="white mb-50">
        <v-ons-col width="20%">
        </v-ons-col>
        <v-ons-col width="20%">
          <span class="social_txt">Line</span>
        </v-ons-col>
        <v-ons-col width="20%">
          <span class="social_txt">QRコード</span>
        </v-ons-col>
        <v-ons-col width="20%">
          <span class="social_txt">コピー</span>
        </v-ons-col>
        <v-ons-col width="20%">
        </v-ons-col>
      </v-ons-row>
    </v-ons-action-sheet>
    <v-ons-alert-dialog modifier="rowfooter"
        :visible.sync="deleteMSG"
    >
      <span slot="title" class="title">つながりの解除</span>
      <p class="content">本当に「優子さん」とのつながり
を解除しますか？</p>
      <template slot="footer">
        <v-ons-alert-dialog-button @click="deleteMSG = false"><span class="cancel">キャンセル</span></v-ons-alert-dialog-button>
        <v-ons-alert-dialog-button @click="deletePermanantly"><span class="ok">削除</span></v-ons-alert-dialog-button>
      </template>
    </v-ons-alert-dialog>

  </v-ons-page>
</template>

<script>
  export default {
    name: "familysetting",
    data(){
      return{
        deleteMSG: false,
        inviteMethodFlag: false,
        //registered_family: [],
        registered_family: ['優子', '隆'],
      }
    },
    methods: {
      deletefamily(){
        this.deleteMSG = true;
      },
      deletePermanantly(){
        this.deleteMSG = false;
        this.$ons.notification.toast('つながりが解除されました', {timeout: 2000, class: "text-alignL center"})
      },
      addFamily(){
        this.inviteMethodFlag = true;
      }
    }
  }
</script>

<style scoped>
  .mt-10{
    padding-top: 10px;
  }
  .mb-50{
    padding-bottom: 55px;
  }
  .social_txt{
    font-family: "SF Pro Display";
    font-style: normal;
    font-weight: normal;
    font-size: 12px;
    line-height: 150%;
    display: flex;
    align-items: center;
    color: #8293A3;
    justify-content: center;
  }
  .white{
    background: white;
  }
  .social{
    border-radius: 50%;
    width: 44px;
    height: 44px;
  }
  .tab-bottom {
    display: flex;
    justify-content: space-around;
    padding-top: 1rem;
    padding-bottom: 2rem;
    background: white;
    border-top: 1px solid lightgray;
    border-top-left-radius: 0.5rem;
    border-top-right-radius: 0.5rem;
  }
  .tool_bottom{
    height: 82px;
    padding: 0px 40px;
  }
  .no_family{
    justify-content: center !important;
    font-family: "Noto Sans CJK JP";
    font-style: normal;
    font-weight: normal;
    font-size: 12px;
    line-height: 150%;
    color: #8293A3;
    text-align: center;
    padding: 30px 0px;
  }
  .title{
    font-family: "SF Pro Text";
    font-style: normal;
    font-weight: 600;
    font-size: 17px;
    line-height: 22px;
    letter-spacing: -0.408px;
    color: #000000;
  }
  .content{
    font-family: "SF Pro Text";
    font-style: normal;
    font-weight: normal;
    font-size: 13px;
    line-height: 16px;
    letter-spacing: -0.078px;
    color: #000000;
    margin: 0px 18px;
  }
  .ok{
    color: red;
  }
  .ml-21{
    vertical-align: super;
    margin-left: 21px;
  }
  .ml-30{
    margin-left: 5px;
  }
  .abt_top-32{
    margin-top: 16px;
    font-family: "Noto Sans JP";
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 150%;
    color: #0089FF;
  }
  .lst_content_right{
    font-family: "Noto Sans JP";
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 150%;
    color: #EA3223;
  }
  .lst_content_left{
    font-family: "Noto Sans JP";
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 150%;
    color: #303235;
  }
  .lst_title{
    font-family: "Noto Sans CJK JP";
    font-style: normal;
    font-weight: bold;
    font-size: 12px;
    line-height: 150%;
    color: #193342;
  }
  .family_list{
    margin-top: 45px;
  }
  .header{
    border-bottom: 1px solid lightgrey;
    height: 88px;
    padding-top: 40px;
  }
  .h_left{
    margin-left: 0px;
    margin-top: 10px;
  }
  .h_right{
    float: right;
    margin-top: 10px;
    margin-right: 5px;
  }
  .h_title{
    margin-top: 12px;
    font-family: "Noto Sans JP";
    font-style: normal;
    font-weight: bold;
    font-size: 18px;
    line-height: 26px;
    color: #303235;
  }

</style>
