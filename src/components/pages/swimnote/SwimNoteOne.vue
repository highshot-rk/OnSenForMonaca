<template>
  <v-ons-page>
    <div style="position: relative;">
      <img style="width: 100%;height: auto;" src="static/assets/images/practice01.png" />
      <span @click="goBack()" style="position: absolute; left: 5px; top: 3rem;color: white;" class="material-icons">arrow_back</span>
      <span style="position: absolute;bottom: 6.5rem;left: 1rem;color: white;font-size: 1.5rem;font-weight: bold;">03.17</span>
      <span style="position: absolute;bottom: 6.5rem;left: 5rem;color: white;">月</span>
      <span style="position: absolute;bottom: 5rem;left: 1rem;color: white;">2021</span>
      <div style="position: absolute;bottom: 0.1rem;left: 1rem;display: flex;justify-content: center;font-size: 0.6rem;">
        <p style="color: white;margin-right: 1rem;">総距離</p>
        <p style="color: white;margin-right: 1rem;">1,000m</p>
        <p style="color: white;margin-right: 1rem;">総時間</p>
        <p style="color: white;margin-right: 1rem;">2h45m</p>
      </div>
      <div style="position: absolute;bottom: 3rem;display: flex; left: 1rem;">
        <v-ons-button style="background: white;color: #5496D7;font-size:0.8rem;border-radius: 100px;height: 24px;display: flex;justify-content: center;align-items: center;margin-right: 0.3rem;">メニュー名1</v-ons-button>
        <v-ons-button style="background: white;color: #5496D7;font-size:0.8rem;border-radius: 100px;height: 24px;display: flex;justify-content: center;align-items: center;margin-right: 0.3rem;">メニュー名2</v-ons-button>
        <v-ons-button style="background: white;color: #5496D7;font-size:0.8rem;border-radius: 100px;height: 24px;display: flex;justify-content: center;align-items: center;margin-right: 0.3rem;">メニュー名3</v-ons-button>
      </div>
    </div>
    <div style="position: relative;padding: 10px;">
      <div style="position: absolute;top: 0;left: 0; right: 0; height: 100%;z-index:-1;">
        <div style="margin: 30px; border-left: 2px solid #8293A3;height: 100%;"></div>
      </div>
      <div class="standard-item">
        <div style="background: #5496D7;border-radius: 100px;width: fit-content;padding: 10px;color: white;display: flex;justify-content: center;margin-right: 10px;">
          <span class="material-icons">flag</span>
        </div>
        <span style="color: #5496D7;flex: 1 1 auto;font-weight: bold;">練習開始</span>
        <span style="color: #707070;font-size: 0.7rem;">12:35</span>
      </div>
      <div class="standard-item">
        <div style="background: #E9A904;border-radius: 100px;width: fit-content;padding: 10px;color: white;display: flex;justify-content: center;margin-right: 10px;">
          <span class="material-icons">sports</span>
        </div>
        <span style="color: #5496D7;flex: 1 1 auto;font-weight: bold;">準備体操</span>
        <span style="color: #707070;font-size: 0.7rem;">12:35</span>
      </div>
      <div class="standard-item">
        <div style="background: #5496D7;border-radius: 100px;width: fit-content;padding: 10px;color: #0089FF;display: flex;justify-content: center;margin-right: 10px;">
          <span class="material-icons">pool</span>
        </div>
        <span style="color: #5496D7;flex: 1 1 auto;font-weight: bold;">練習名スタート</span>
        <span style="color: #707070;font-size: 0.7rem;">12:35</span>
      </div>
      <template v-for="(player, index) in playerList">
        <div :key="index" class="player-item">
          <div style="border-radius: 100px;width: 44px;color: #0089FF;display: flex;justify-content: center;margin-right: 10px;">
            <img width="34px" height="34px" :src="player.img" alt="">
          </div>
          <div style="flex: 1 1 auto;font-weight: bold;">
            <span style="color: #707070;font-size: 0.9rem;">{{player.name}}</span>
            <p style="margin: 0;color: #303235;">{{player.status}}</p>
          </div>
          <span style="color: #707070;font-size: 0.7rem;">12:35</span>
        </div>
      </template>
    </div>
  </v-ons-page>
</template>

<script>
export default {
  data(){
    return {
      playerList: [
        {img: "static/assets/images/tempimg1.png", name: "ひまり", status: "ラップ1 スタート", time: "12:35"},
        {img: "static/assets/images/tempimg1.png", name: "ひまり", status: "ラップ1 スタート", time: "12:35"},
        {img: "static/assets/images/tempimg1.png", name: "ひまり", status: "ラップ1 スタート", time: "12:35"},
        {img: "static/assets/images/tempimg1.png", name: "ひまり", status: "ラップ1 スタート", time: "12:35"},
        {img: "static/assets/images/tempimg1.png", name: "ひまり", status: "ラップ1 スタート", time: "12:35"},
        {img: "static/assets/images/tempimg1.png", name: "ひまり", status: "ラップ1 スタート", time: "12:35"},
        {img: "static/assets/images/tempimg1.png", name: "ひまり", status: "ラップ1 スタート", time: "12:35"},
        {img: "static/assets/images/tempimg1.png", name: "ひまり", status: "ラップ1 スタート", time: "12:35"},
        {img: "static/assets/images/tempimg1.png", name: "ひまり", status: "ラップ1 スタート", time: "12:35"},
        {img: "static/assets/images/tempimg1.png", name: "ひまり", status: "ラップ1 スタート", time: "12:35"},
      ]
    };
  },
  methods: {
    goBack() {
      this.push_screen.pop();
    }
  }
}
</script>

<style scoped>
  .standard-item {
    display: flex;
    align-items: center;
    margin-bottom: 20px
  }
  .player-item {
    display: flex;
    margin-bottom: 20px
  }
</style>
