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
      <div class="lane-group" style="opacity: 1">
        <template v-for="(action, key) in actions">
          <div
            :key="key"
            class="round-box"
            :style="{background: actions_bg[key], border: 'none', 'padding-top': '0.6rem', 'padding-bottom': '0.6rem', }"
            @click="re_execute_menu = true"
          >
            <div style="display: flex;align-items: center;justify-content: center;">
              <img :src="slanes[key].img" style="width: 24px; height: 24px;"/>
              <p class="white-color" style="margin-left: 10px">{{slanes[key].name}}</p>
            </div>
            <p class="white-color">{{action}}</p>
          </div>
        </template>
      </div>
      <div class="lane-group" style="margin-top: 5px;">
        <template v-for="(lane, key) in lane_info">
          <div
            :key="key"
            class="round-box"
            :style="{background: actions1_bg[key], border: 'none', 'padding-top': '0.6rem', 'padding-bottom': '0.6rem', opacity: lane.img == '' ? 0.2 : 1}"
            @click="end_menu = true"
          >
            <p class="white-color"><b>{{lane.set}}</b></p>
            <p class="white-color">{{lane.rank}}</p>
            <div style="display: flex;align-items: center;justify-content: center;">
              <template v-if="lane.img != ''">
                <img :src="lane.img" style="width: 24px; height: 24px;"/>
                <p class="white-color" style="margin-left: 10px">{{lane.name}}</p>
              </template>
              <template v-if="lane.img == ''">
                <div style="background: white; width: 24px; height: 24px;border-radius: 100px"/>
                <p class="white-color" style="margin-left: 10px">------</p>
              </template>
            </div>
            <h2 style="text-align: center;" class="white-color">{{lane.mark}}</h2>
          </div>
        </template>
      </div>
      <div class="lane-group" style="margin-top: 5px;opacity: 0.2">
        <template v-for="(action, key) in actions1">
          <div
            :key="key"
            class="round-box"
            :style="{background: actions1_bg[key], border: 'none', 'padding-top': '0.6rem', 'padding-bottom': '0.6rem', }"
            @click="del_menu = true"
          >
            <p class="white-color">{{action}}</p>
          </div>
        </template>
      </div>
    </div>
    <v-ons-alert-dialog modifier="rowfooter"
      :visible.sync="re_execute_menu"
    >
      <p slot="title" class="title" style="font-weight: bold;">メニュー実施をやり直します</p>
      <span class="content">実行中のデータは消去されます。</span><br/>
      <span>よろしいですか？。</span>
      <template slot="footer">
        <v-ons-alert-dialog-button @click="re_execute_menu = false"><span class="cancel">キャンセル</span></v-ons-alert-dialog-button>
        <v-ons-alert-dialog-button @click="re_execute_menu = false"><span class="ok">やり直す</span></v-ons-alert-dialog-button>
      </template>
    </v-ons-alert-dialog>
    <v-ons-alert-dialog modifier="rowfooter"
      :visible.sync="end_menu"
    >
      <p slot="title" class="title" style="font-weight: bold;">メニュー実施を終了します</p>
      <span class="content">本当に「メニュー1」を終了しますか？</span>
      <template slot="footer">
        <v-ons-alert-dialog-button @click="end_menu = false"><span class="cancel">キャンセル</span></v-ons-alert-dialog-button>
        <v-ons-alert-dialog-button @click="end_menu = false"><span class="ok" style="color: #EA3223;">終了する</span></v-ons-alert-dialog-button>
      </template>
    </v-ons-alert-dialog>
    <v-ons-alert-dialog modifier="rowfooter"
      :visible.sync="del_menu"
    >
      <p slot="title" class="title" style="font-weight: bold;">メニュー実施を終了します</p>
      <span class="content">「メニュー1」実施が終了しました。</span><br />
      <span>練習ページに移動しますか？</span><br/>
      <span>次の「メニュー」を実施しますか？</span>
      <template slot="footer">
        <v-ons-alert-dialog-button @click="del_menu = false"><span class="cancel">練習ページ</span></v-ons-alert-dialog-button>
        <v-ons-alert-dialog-button @click="del_menu = false"><span class="ok">次のメニュー</span></v-ons-alert-dialog-button>
      </template>
    </v-ons-alert-dialog>
  </div>
</template>

<script>
export default {
  name: 'menu-1',
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
      actions: ["やり直し", "やり直し", "やり直し"],
      actions_bg: ["#29B9E7", "#E99B04", "#E45A8C"],
      slanes: [
        {img: "/static/assets/images/lane-temp-player.png", name: "ひなこ"},
        {img: "/static/assets/images/lane-temp-player.png", name: "よしお"},
        {img: "/static/assets/images/lane-temp-player.png", name: "みゆき"},
      ],
      lane_info: [
        {set: "セット＃1", rank: "1本目", img: "/static/assets/images/lane-temp-player.png", name: "たかし", mark: "12"},
        {set: "セット＃1", rank: "1本目", img: "/static/assets/images/lane-temp-player.png", name: "たかし", mark: "15"},
        {set: "セット＃1", rank: "1本目", img: "", name: "", mark: ""}
      ],
      actions1: ["スキップ", "スキップ", "スキップ"],
      actions1_bg: ["#29B9E7", "#E99B04", "#E45A8C"],
      re_execute_menu: false,
      end_menu: false,
      del_menu: false,
    }
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
