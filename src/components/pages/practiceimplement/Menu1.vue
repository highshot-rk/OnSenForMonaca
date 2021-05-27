<template>
  <div>
    <div class="header-bar">
      <p>
        メニュー1
      </p>
      <span style="position: absolute;right: 5px;top: 1rem;" class='material-icons'>menu_book</span>
    </div>
    <div class="container">
      <p>計測タイム</p>
      <div class="lane-group">
        <template v-for="(laneone, key) in lanes">
          <div :key="key" class="round-box" :style="{'border-color': laneone.color}">
            <p :style="{color: laneone.color}">レーン1</p>
            <p style="min-height: 15px">{{laneone.no}}</p>
            <p style="font-size: 1.1rem; font-weight: bold; min-height: 21px;">{{laneone.time}}</p>
            <p style="min-height: 15px">{{laneone.name}}</p>
          </div>
        </template>
      </div>
      <p>次の泳者カウントダウン</p>
      <div class="lane-group">
        <template v-for="(swimmer, key) in swimmers">
          <div :key="key" class="round-box" style="background: #EFF3F6; border: none;">
            <p>{{swimmer.set}}</p>
            <p>{{swimmer.rank}}</p>
            <p class="name">{{swimmer.name}}</p>
            <p>{{swimmer.time}}</p>
          </div>
        </template>
      </div>
      <div style="height: 1.5rem;"></div>
      <div class="lane-group" style="opacity: 0.2">
        <template v-for="(action, key) in actions">
          <div :key="key" class="round-box" :style="{background: actions_bg[key], border: 'none', 'padding-top': '0.6rem', 'padding-bottom': '0.6rem', }">
            <p class="white-color">{{action}}</p>
          </div>
        </template>
      </div>
      <div class="lane-group" style="margin-top: 5px;">
        <template v-for="(lane, key) in lane_info">
          <div
          :key="key"
          class="round-box"
          :style="{background: actions1_bg[key], border: 'none', 'padding-top': '0.6rem', 'padding-bottom': '0.6rem', }"
          @click="showModal()">
            <p class="white-color"><b>{{lane.set}}</b></p>
            <p class="white-color">{{lane.rank}}</p>
            <div style="display: flex;align-items: center;justify-content: center;">
              <img :src="lane.img" style="width: 24px; height: 24px;"/>
              <p class="white-color" style="margin-left: 10px">{{lane.name}}</p>
            </div>
            <h2 style="text-align: center;" class="white-color">{{lane.mark}}</h2>
          </div>
        </template>
      </div>
      <div class="lane-group" style="margin-top: 5px;opacity: 0.2">
        <template v-for="(action, key) in actions1">
          <div :key="key" class="round-box" :style="{background: actions1_bg[key], border: 'none', 'padding-top': '0.6rem', 'padding-bottom': '0.6rem', }">
            <p class="white-color">{{action}}</p>
          </div>
        </template>
      </div>
    </div>
    <v-ons-modal :visible="modalVisible" @click="modalVisible = false">
      <div style="background: white; border-radius: 1rem;color: black;padding: 1rem;min-height: 50vh; margin: 1rem;">
        <p style="font-weight: bold">右レーン２番の結果</p>
        <p style="color: #8293A3;">（みゆき）</p>
        <table style="text-align: center; width: 100%">
          <tbody>
            <tr>
              <td style="font-weight: 700;">ベスト</td>
              <td>：</td>
              <td style="color: #0089FF;">20.87 (1セット1本目)</td>
            </tr>
            <tr>
              <td style="font-weight: 700;">ベスト</td>
              <td>：</td>
              <td style="color: #EA3223;">20.87 (1セット1本目)</td>
            </tr>
          </tbody>
        </table>
        <p style="font-weight: bold;">直近10本の結果</p>
        <div style="display: flex;justify-content: space-around;">
          <div>セット</div>
          <div>本日</div>
          <div>タイム</div>
        </div>
        <div style="display: flex;justify-content: space-around;">
          <div>1</div>
          <div>1</div>
          <div>20.98</div>
        </div>
      </div>
    </v-ons-modal>
    <v-ons-modal :visible="modalVisible1" @click="modalVisible1 = false">
      <span style="position: absolute;right: 5px;top: 1rem;" class='material-icons'>close</span>
      <div style="display: flex; justify-content: center; align-items: center;flex-direction: column;">
        <v-ons-button
          style="border-radius: 100px;background: white; color: #0089FF;margin-bottom: 1rem;width: 80vw;display: flex; align-items: center; justify-content: center;"
        >
          <span style="margin: " class='material-icons'>menu</span>
          人数とレーンを変更
        </v-ons-button>
        <v-ons-button
          style="border-radius: 100px;background: white; color: #0089FF;margin-bottom: 1.5rem;width: 80vw;display: flex; align-items: center; justify-content: center;">
          <span class='material-icons'>menu</span>
          実施方法設定
        </v-ons-button>
        <v-ons-button
          style="border-radius: 100px;background: #0089FF; color: #FFFFFF;margin-bottom: 1rem;width: 80vw;">
          実施方法設定
        </v-ons-button>
      </div>
      <v-ons-button
        style="position: absolute;bottom: 3rem;left: 50%; transform: translateX(-50%);border-radius: 100px; border: 2px solid white;background: transparent; color: #FFFFFF;margin-bottom: 1rem;width: fit-content;display: flex; align-items: center; justify-content: center;">
        <span class='material-icons'>menu</span>
        実施方法設定
      </v-ons-button>
    </v-ons-modal>
  </div>
</template>

<script>
import Modal from '../top/components/Modal';
export default {
  name: 'menu-1',
  components: {
    Modal,
  },
  data () {
    return {
      lanes: [
        {no: "1番", time: "17.22", name: "ひなこ", lane: "レーン1", color: "#29B9E7"},
        {no: "1番", time: "19.54", name: "よしお", lane: "レーン2", color: "#E99B04"},
        {no: "1番", time: "21.32", name: "みゆき", lane: "レーン3", color: "#E45A8C"},
      ],
      swimmers: [
        {set: "セット＃1", rank: "1本目", name: "たかし", time: "5秒前"},
        {set: "セット＃1", rank: "1本目", name: "ひまり", time: "5秒前"},
        {set: "セット＃1", rank: "1本目", name: "ともき", time: "5秒前"},
      ],
      actions: ["やり直し", "Redo", "Redo"],
      actions_bg: ["#29B9E7", "#E99B04", "#E45A8C"],
      lane_info: [
        {set: "セット＃1", rank: "1本目", img: "/static/assets/images/lane-temp-player.png", name: "たかし", mark: "0"},
        {set: "セット＃1", rank: "1本目", img: "/static/assets/images/lane-temp-player.png", name: "たかし", mark: "0"},
        {set: "セット＃1", rank: "1本目", img: "/static/assets/images/lane-temp-player.png", name: "たかし", mark: "0"}
      ],
      actions1: ["スキップ", "スキップ", "スキップ"],
      actions1_bg: ["#29B9E7", "#E99B04", "#E45A8C"],
      modalVisible: false,
      modalVisible1: true,
    }
  },
  methods: {
    showModal() {
      this.modalVisible = true;
    },
    showModal1() {
      this.modalVisible1 = true;
    },
  }
}
</script>

<style scoped>
  .header-bar {
    padding: 0.1rem 0.7rem;
    box-shadow: inset 0px -1px 0px rgba(0, 0, 0, 0.05);
    background: #FFFFFF;
  }
  .header-bar p {
    text-align: center;
    font-weight: bold;
  }
  .container {
    padding-left: 0.6rem;
    padding-right: 0.6rem;
  }
  p {
    text-align: center;
  }
  .lane-group {
    display: flex;
    justify-content: space-evenly;
  }
  .lane-group .round-box {
    border-radius: 0.4rem;
    border: 1px solid black;
    width: 27vw;
  }
  .lane-group p {
    color: #707070;
    margin-top: 0.5rem;
    margin-bottom: 0.5rem;
    font-size: 0.7rem;
  }
  .lane-group .name {
    color: #5496D7;
  }
  p.white-color, h2.white-color {
    color: white;
  }
</style>
