<template>
  <v-ons-page>
    <div style="position: relative;">
      <img style="width: 100%;height: auto;" src="static/assets/images/practice01.png" />
      <span style="position: absolute; left: 5px; top: 3rem;color: white;" class="material-icons">arrow_back</span>
      <p style="text-align: center;width: 100%;position: absolute;top: 3rem; color: white;margin-top: 0;margin-bottom: 0;">SWIM NOTE</p>
      <span style="position: absolute;bottom: 4rem;left: 1rem;color: white;font-size: 1.5rem;font-weight: bold;">03.17</span>
      <span style="position: absolute;bottom: 4rem;left: 5rem;color: white;">月</span>
      <span style="position: absolute;bottom: 2.5rem;left: 1rem;color: white;">2021</span>
      <div style="position: absolute;bottom: 0.1rem;left: 1rem;display: flex;justify-content: center;font-size: 0.6rem;">
        <p style="color: white;margin-right: 1rem;">総距離</p>
        <p style="color: white;margin-right: 1rem;">1,000m</p>
        <p style="color: white;margin-right: 1rem;">総時間</p>
        <p style="color: white;margin-right: 1rem;">2h45m</p>
      </div>
      <span style="position: absolute;bottom: 4rem;right: 1rem;color: white;">スイムラブスコア</span>
      <img style="position: absolute;bottom: 1rem;right: 7rem;" src="static/assets/icons/C.png" alt="">
      <span style="position: absolute;bottom: 1rem;right: 5rem;color: white;">50</span>
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
    <div class="container">
      <p style="margin-bottom: 10px;">参加者：12名</p>
      <div class='my-carousel'>
        <div @click="selectPlayer(-1)" :class="{'active': -1 == selectedPlayer}" style="">
          <div style="display: flex; justify-content: center; align-items: center;padding: 1rem;background: #5496D7;border-radius: 100px;width: fit-content;color: white;border: 4px solid white;">
            <span class="material-icons">leaderboard</span>
          </div>
          <p style="text-align: center;font-weight: 500;margin: 5px 0;color: #0089FF;font-size:0.8rem;">チーム平均</p>
        </div>
        <div @click="selectPlayer(index)" :class="{'active': index == selectedPlayer}" :key="index" v-for="(img1, index) in img1s">
          <div style="position: relative;">
            <img style="width: 64px; height: 64px;" :src="img1.img" alt="">
            <span style="color: gray;position: absolute; right: 0;top:0;background-color: yellow;border-radius:50%;" class="material-icons">{{img1.emoji}}</span>
            <p style="text-align: center;font-weight: 500;margin: 5px;font-size:0.8rem;">{{img1.name}}</p>
          </div>
        </div>
      </div>
    </div>

    <div :key="chartindex" v-for="(data, chartindex) in chartDatas">
      <p style="margin-left: 15px;">18:35分開始〜</p>
      <v-ons-card style="padding: 10px;">
        <p style="font-weight: bold;margin: 0;">メニュー #1</p>
        <div style="display: flex;align-items: center;color: #707070;font-size: 0.9rem;">
          <span style="margin-right: 10px;">距離</span>
          <span style="margin-right: 10px;">1,000m</span>
          <span style="margin-right: 10px;">時間</span>
          <span style="margin-right: 10px;">0h30m</span>
        </div>
        <div class="panel">
          <template v-for="(info, index) in panelInfo">
            <div :key="index" class="item">
              <p style="color: #8293A3;">{{info.jp}}</p>
              <p style="color: #5496D7;">{{info.en}}</p>
            </div>
          </template>
        </div>
      </v-ons-card>
      <v-ons-card style="padding: 0px;margin: 0;">
        <apex-chart></apex-chart>
      </v-ons-card>
    </div>
  </v-ons-page>
</template>

<script>
import ApexChart from './ApexChart'
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
        0,1,2,3
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
    margin: 0;
  }
  .active div img {
    border: 2px solid white;
    border-radius: 100px;
  }
  .active div p {
    color: #0089FF;
  }
</style>
