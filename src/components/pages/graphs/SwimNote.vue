<template>
  <v-ons-page>
    <div style="position: relative;">
      <img style="width: 100%;height: auto;" src="static/assets/images/practice01.png" />
      <span style="position: absolute; left: 5px; top: 3rem;color: white;" class="material-icons">arrow_back</span>
      <p style="text-align: center;width: 100%;position: absolute;top: 3rem; color: white;margin-top: 0;margin-bottom: 0;">SWIM NOTE</p>
      <span style="position: absolute;bottom: 4rem;left: 1rem;color: white;font-size: 1.5rem;font-weight: bold;">03.17</span>
      <span style="position: absolute;bottom: 4rem;left: 5rem;color: white;">月</span>
      <span style="position: absolute;bottom: 2.5rem;left: 1rem;color: white;font-size: 0.8rem;">2021</span>
      <div style="position: absolute;bottom: 0.1rem;left: 1rem;display: flex;justify-content: center;font-size: 0.6rem;">
        <p style="color: white;margin-right: 1rem;">総距離</p>
        <p style="color: white;margin-right: 1rem;">1,000m</p>
        <p style="color: white;margin-right: 1rem;">総時間</p>
        <p style="color: white;margin-right: 1rem;">2h45m</p>
      </div>
      <v-ons-button style="background: white;color: #0089FF;border-radius: 100px;position: absolute;right: 0.5rem;  bottom: 0.5rem;display: flex; align-items: center;font-size: 0.7rem;height: 28px;"><span class="material-icons">loop</span>更新</v-ons-button>
    </div>
    <v-ons-carousel swipeable overscrollable
        item-width="30%" style="padding: 0"
    >
      <v-ons-carousel-item v-for="(item, index) in this.items" :key="index" class="carousel-list" style="padding:0.2rem;">
          <img :src=item width="100%" style="border-radius: 3px;">
      </v-ons-carousel-item>
      <v-ons-carousel class="carousel-list">
      </v-ons-carousel>
    </v-ons-carousel>

    <div :key="chartindex" v-for="(data, chartindex) in chartDatas">
      <p style="margin-left: 15px;color: #707070;margin-bottom: 0.5rem;">18:35分開始〜</p>
      <v-ons-card style="padding: 15px;margin: 0;">
        <p style="font-weight: bold;margin: 0;">メニュー #1</p>
        <div style="display: flex;align-items: center;color: #707070;font-size: 0.9rem;">
          <span style="margin-right: 10px;">距離</span>
          <span style="margin-right: 10px;">1,000m</span>
          <span style="margin-right: 10px;">時間</span>
          <span style="margin-right: 10px;">0h30m</span>
        </div>
        <div class="panel">
          <template v-for="(info, index) in panelInfo">
            <div :key="'a' + index" class="item">
              <p style="color: #8293A3;">{{info.jp}}</p>
              <p style="color: #5496D7;">{{info.en}}</p>
            </div>
          </template>
        </div>
        <hr />
        <div style="background: #5496D710;display: relative;margin-left:0px;margin-right: 0px;">
          <apex-chart></apex-chart>
        </div>
        <v-ons-row style="font-size: 0.8rem;text-align: center;color: #8293A3;">
          <v-ons-col class="20%" style="padding: 10px;">
            セット
          </v-ons-col>
          <v-ons-col class="20%" style="padding: 10px;">
            距離
          </v-ons-col>
          <v-ons-col class="20%" style="padding: 10px;">
            本数
          </v-ons-col>
          <v-ons-col class="20%" style="padding: 10px;">
            サイクル
          </v-ons-col>
          <v-ons-col class="20%" style="padding: 10px;">
            セット間
          </v-ons-col>
        </v-ons-row>
        <v-ons-row style="font-size: 0.8rem;text-align: center;background: #F1F7FC;color: #5496D7;">
          <v-ons-col class="20%" style="padding: 10px;">
            #1
          </v-ons-col>
          <v-ons-col class="20%" style="padding: 10px;">
            50
          </v-ons-col>
          <v-ons-col class="20%" style="padding: 10px;">
            4
          </v-ons-col>
          <v-ons-col class="20%" style="padding: 10px;">
            10
          </v-ons-col>
          <v-ons-col class="20%" style="padding: 10px;">
            0
          </v-ons-col>
        </v-ons-row>
        <v-ons-row style="font-size: 0.8rem;text-align: center;background: #F1F7FC;margin-top:5px;;color: #5496D7;">
          <v-ons-col class="20%" style="padding: 10px;">
            #1
          </v-ons-col>
          <v-ons-col class="20%" style="padding: 10px;">
            50
          </v-ons-col>
          <v-ons-col class="20%" style="padding: 10px;">
            4
          </v-ons-col>
          <v-ons-col class="20%" style="padding: 10px;">
            10
          </v-ons-col>
          <v-ons-col class="20%" style="padding: 10px;">
            0
          </v-ons-col>
        </v-ons-row>
      </v-ons-card>
    </div>


    <div :key="chartindex" v-for="(data, chartindex) in tableDatas">
      <p style="margin-left: 15px;">18:35分開始〜</p>
      <v-ons-card style="padding: 10px;">
        <p style="font-weight: bold;margin: 0;">メニュー #1</p>
        <div class="panel">
          <template v-for="(info, index) in panelInfo">
            <div :key="'chartindex' + index" class="item">
              <p style="color: #8293A3;">{{info.jp}}</p>
              <p style="color: #5496D7;">{{info.en}}</p>
            </div>
          </template>
        </div>
        <hr/>
        <v-ons-row style="color: #8293A3;font-size: 0.8rem;text-align: center;">
          <v-ons-col class="20%" style="padding: 10px;">
            セット
          </v-ons-col>
          <v-ons-col class="20%" style="padding: 10px;">
            距離
          </v-ons-col>
          <v-ons-col class="20%" style="padding: 10px;">
            本数
          </v-ons-col>
          <v-ons-col class="20%" style="padding: 10px;">
            サイクル
          </v-ons-col>
          <v-ons-col class="20%" style="padding: 10px;">
            セット間
          </v-ons-col>
        </v-ons-row>
        <v-ons-row style="color: #0089FF;font-size: 0.8rem;text-align: center;background: #F1F7FC;">
          <v-ons-col class="20%" style="padding: 10px;">
            #1
          </v-ons-col>
          <v-ons-col class="20%" style="padding: 10px;">
            50
          </v-ons-col>
          <v-ons-col class="20%" style="padding: 10px;">
            4
          </v-ons-col>
          <v-ons-col class="20%" style="padding: 10px;">
            10
          </v-ons-col>
          <v-ons-col class="20%" style="padding: 10px;">
            0
          </v-ons-col>
        </v-ons-row>
        <v-ons-row style="color: #0089FF;font-size: 0.8rem;text-align: center;background: #F1F7FC;">
          <v-ons-col class="20%" style="padding: 10px;">
            #1
          </v-ons-col>
          <v-ons-col class="20%" style="padding: 10px;">
            50
          </v-ons-col>
          <v-ons-col class="20%" style="padding: 10px;">
            4
          </v-ons-col>
          <v-ons-col class="20%" style="padding: 10px;">
            10
          </v-ons-col>
          <v-ons-col class="20%" style="padding: 10px;">
            0
          </v-ons-col>
        </v-ons-row>
        <hr />
        <v-ons-row>
          <v-ons-col style="color: #0089FF;display:flex;align-items: center;">
            <span class="material-icons">expand_less</span>
            <span>セット数:2</span>
          </v-ons-col>
        </v-ons-row>
      </v-ons-card>
    </div>
  </v-ons-page>
</template>

<script>
import ApexChart from '../swimnote/ApexChart'
export default {
  components: {
    ApexChart,
  },
  data () {
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
      img1s: [
        {img: "static/assets/images/tempimg1.png", emoji: "sentiment_satisfied", name: "ひまり"},
        {img: "static/assets/images/tempimg1.png", emoji: "sentiment_very_satisfied", name: "田中"},
        {img: "static/assets/images/tempimg1.png", emoji: "sentiment_satisfied", name: "たけ"},
        {img: "static/assets/images/tempimg1.png", emoji: "sentiment_very_satisfied", name: "せや"},
        {img: "static/assets/images/tempimg1.png", emoji: "sentiment_satisfied", name: "ひまり"},
        {img: "static/assets/images/tempimg1.png", emoji: "sentiment_very_satisfied", name: "ひまり"},
        {img: "static/assets/images/tempimg1.png", emoji: "sentiment_satisfied", name: "ひまり"},
        {img: "static/assets/images/tempimg1.png", emoji: "sentiment_very_satisfied", name: "ひまり"},
      ],
      panelInfo: [
        {jp: "種類", en: "Swim"},
        {jp: "種目", en: "Choice"},
        {jp: "内容", en: "Drill"},
        {jp: "強度", en: "EN1"},
      ],
      chartDatas: [
        0,1,
      ],
      tableDatas: [
        0,1
      ],
      selectedPlayer: -1,
    }
  },
  methods: {
    selectPlayer(id) {
      this.selectedPlayer = id;
    }
  }
}
</script>

<style scoped>
  .container {
    padding: 10px;
  }
  .my-carousel {
    display: flex;
    flex-direction: row;
    width: 100%;
    overflow: scroll;
    scrollbar-color: blue;
  }
  .my-carousel > * {
    padding: 5px;
  }
  .panel {
    background: #5496D711;
    display: flex;
    justify-content: space-around;
    padding: 10px;
  }
  .panel .item {
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;
  }
  .panel .item p {
    margin: 5px;
  }
  .active div img {
    border: 2px solid white;
    border-radius: 100px;
  }
  .active div p {
    color: #0089FF;
  }
  hr {
    border: 1px solid #5496D7;
    opacity: 0.2;
  }
</style>
