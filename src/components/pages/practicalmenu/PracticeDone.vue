<template>
  <v-ons-page>
    <v-ons-toolbar class="header">
        <div class="left"><v-ons-back-button modifier="quiet" class=" h_left"><span class="material-icons">west</span></v-ons-back-button></div>
        <div class="left toolbar__left">
          <p style="margin: 0" class="h_title">2021.03.17月の練習</p>
          <p style="margin: -15px 0">07:30  -    /   ロンド成増</p>
        </div>
        <div class="right" style="width: 40%;">
          <v-ons-button modifier="quiet" class=" h_right"><span class="material-icons">content_copy</span></v-ons-button>
          <v-ons-button modifier="quiet" class=" h_right" @click="confirm_download = !confirm_download">
            <span class="material-icons">content_copy</span>
          </v-ons-button>
        </div>
    </v-ons-toolbar>
    <p @click="changeRunningStatus()" :style="{background: running ? '#E9A904' : '#5496D7'}" style="margin: 2.7rem 0 0 0; padding: 5px; color: white; text-align: center;">
      {{ running ? "実施中" : "実施済"}}
    </p>
    <v-ons-card>
      <p style="text-align: center;color: #8293A3;margin: 0;">参加者</p>
      <div style="display:flex;justify-content: center;">
        <img style="width: 24px;height: 24px;" src="/static/assets/images/tempimg2.png" alt="">
        <img style="width: 24px;height: 24px;" src="/static/assets/images/tempimg1.png" alt="">
        <img style="width: 24px;height: 24px;" src="/static/assets/images/tempimg2.png" alt="">
        <img style="width: 24px;height: 24px;" src="/static/assets/images/tempimg1.png" alt="">
        <div style="background: #707070;border-radius:100px;color:white;width: 24px; height: 24px;font-size: 0.8rem;display: flex;align-items: center;"><span>+12</span></div>
      </div>
    </v-ons-card>
    <v-ons-row>
      <v-one-col style="width: 50%">
        <v-ons-card>
          <p style="text-align: center;color: #8293A3;margin: 0;">総距離</p>
          <h6 style="margin: 0; text-align: center;">4,000m</h6>
        </v-ons-card>
      </v-one-col>
      <v-one-col style="width: 50%">
        <v-ons-card>
          <p style="text-align: center;color: #8293A3;margin: 0;">総時間</p>
          <h6 style="margin: 0; text-align: center;">2h45m</h6>
        </v-ons-card>
      </v-one-col>
    </v-ons-row>
    <v-ons-card class="card-item">
      <v-ons-carousel swipeable overscrollable
          item-width="30%" style="padding: 0"
      >
          <v-ons-carousel-item v-for="(item, index) in this.items" :key="index" class="carousel-list">
              <img :src=item width="100%" style="margin:0.5rem 0;border-radius: 3px;">
          </v-ons-carousel-item>
          <v-ons-carousel class="carousel-list">
          </v-ons-carousel>
      </v-ons-carousel>
      <p style="margin: 0; color: #0089FF;display: flex;justify-content: center;align-items: center;">
        <span class="material-icons">add</span>
        <span>写真を追加</span>
      </p>
    </v-ons-card>
    <template v-for="(number, index) in menus">
      <menu-card :key="index" :number="number"></menu-card>
    </template>

    <v-ons-bottom-toolbar class="tool_bottom">
      <div class="tab-bottom">
        <div style="text-align: center">
          <v-ons-button modifier="quiet" style="color:#8293A3;">
          <span style="width: 18px; height: 18px; margin: 3px;" class='material-icons'>event_note</span>
          <p style="margin: -10px; font-weight: bold;font-size: 10px;">サマリー</p>
          </v-ons-button>
        </div>
        <div style="text-align: center">
          <v-ons-button modifier="quiet">
          <span style="width: 18px; height: 18px; margin: 3px;" class='material-icons'>edit</span>
          <p style="margin: -10px; font-weight: bold;font-size: 10px;">練習メニュー</p>
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
      :visible.sync="confirm_download"
      cancelable
      title="<span style='font-family: 'Noto Sans JP';
              font-style: normal;
              font-weight: bold;
              font-size: 16px;
              line-height: 150%;
              text-align: center;
              color: #303235;'>2021.03.17月の練習</span>"
    >
      <v-ons-action-sheet-button icon="md-square-o" @click="close_modal()"><span>ダウンロード</span></v-ons-action-sheet-button>

      <v-ons-action-sheet-button icon="md-square-o" @click="close_modal()"><span style="color: #EA3223">削除</span></v-ons-action-sheet-button>

      <v-ons-action-sheet-button icon="md-square-o" @click="close_modal()"><span>キャンセル</span></v-ons-action-sheet-button>
    </v-ons-action-sheet>

  </v-ons-page>
</template>

<script>
import MenuCard from './components/menucard';
export default {
  components: {
    MenuCard
  },
  data(){
    return {
      items: [
          "static/images/practice/practice01.png",
          "static/images/practice/practice02.png",
          "static/images/practice/practice03.png",
          "static/images/practice/practice04.png",
          "static/images/practice/practice05.png",
          "static/images/practice/practice06.png",
          "static/images/practice/practice07.png",
          "static/images/practice/practice08.png",
      ],
      menus: [1,2,3],
      confirm_download: false,
      running: false,
      confirm_start_practice: false,
    }
  },
  methods: {
    changeRunningStatus() {
      this.running = !this.running;
    }
  }
}
</script>

<style scoped>

  .header{
    border-bottom: 1px solid lightgrey;
    height: 88px;
    padding-top: 40px;
  }
  .h_left{
    margin-left: 5px;
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
  ons-card {
    margin: 3px;
  }
  .carousel-list {
      margin-left: 0.2rem;
      margin-right: 0.2rem;
  }
  .card-item {
      text-align: center;
      margin: 0.2rem 0 0 0;
      width: 100%;
      padding: 0.5rem;
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
</style>
