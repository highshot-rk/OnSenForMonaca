<template>
  <div style="padding: 10px;">
    <p style="text-align: center;color: #0089FF;">2021.03.17　選手の評価</p>
    <div style="height: 100vh;overflow: auto;">
      <template v-for="(player, key) in players">
        <div :key="key" style="border-bottom: 1px solid #D3D3D3;position:relative;">
          <img style="position: absolute;width:2rem;height:2rem;" :src="player.img" alt="">
          <p style="margin-left: 2.5rem;padding-top:0.3rem;">{{player.name}}</p>
          <div style="display: flex;justify-content: space-around;align-items: center;padding-bottom: 0.5rem;">
            <template v-for="(mark) in 5">
              <span :key="mark" class='material-icons' style="background: #FEC227;padding: 0;border-radius: 100px;font-size: 3.5rem;" :style="{border: mark == player.evaluation ? '2px solid #29B9E7' : 'none',opacity: mark == player.evaluation ? '1' : '0.4'}">
                {{(mark == 1) ? "sentiment_very_dissatisfied" : (
                  (mark == 2) ? "mood_bad" : (
                    (mark == 3) ? "sentiment_neutral" : (
                      (mark == 4) ? "sentiment_satisfied" : "sentiment_very_satisfied"
                    )
                  )
                )}}
              </span>
            </template>
          </div>
        </div>
      </template>
      <div style="width: 100%;height: 12rem;"></div>
    </div>
    <v-ons-bottom-toolbar style="padding: 10px;height: auto;padding-bottom: 20px;">
      <v-ons-button @click="open_modal = true" style="border-radius: 100px; width: calc(100% - 4rem);margin-left: 2rem; margin-right: 2rem;text-align: center;">完了</v-ons-button>
    </v-ons-bottom-toolbar>

    <v-ons-modal :visible="open_modal" @click="open_modal = false">
      <div style="background: white; opacity: 0.95;width: 100%; height: 100vh;position:absolute;top: 0px;z-index: -1">

      </div>
      <span style="position: absolute;right: 5px;top: 1rem;" class='material-icons'>close</span>
      <div style="display: flex; justify-content: center; align-items: center;flex-direction: column;">
        <p style="color: blue;font-weight: 600">2021.03.17</p>
        <p style="color: black;margin-top: 5px;margin-bottom:5px;">お疲れ様でした！</p>
        <p style="color: black;margin-top: 5px;margin-bottom:5px;">全ての練習が終了しました。</p>
        <p style="color: black;margin-top: 5px;margin-bottom:5px;">選手への評価の記入をお願いします。</p>
      </div>
      <v-ons-button
        style="margin-top: 4rem;border-radius: 100px;background: #0089FF; color: #FFFFFF;margin-bottom: 1rem;">
        評価に進む
      </v-ons-button>
    </v-ons-modal>
  </div>
</template>

<script>
export default {
  data() {
    return {
      players: [
        {id: 1, img: "/static/assets/images/lane-temp-player.png", name: "吉田 花子", evaluation: 5},
        {id: 2, img: "/static/assets/images/lane-temp-player.png", name: "斎藤 優子", evaluation: 5},
        {id: 3, img: "/static/assets/images/lane-temp-player.png", name: "村田 隆", evaluation: 5},
        {id: 4, img: "/static/assets/images/lane-temp-player.png", name: "吉岡 太朗", evaluation: 5},
        {id: 5, img: "/static/assets/images/lane-temp-player.png", name: "宮下優子", evaluation: 5},
        {id: 6, img: "/static/assets/images/lane-temp-player.png", name: "佐藤義行", evaluation: 5},
        {id: 7, img: "/static/assets/images/lane-temp-player.png", name: "村上晴之助", evaluation: 5},
        {id: 7, img: "/static/assets/images/lane-temp-player.png", name: "鈴木竜也", evaluation: 5},
      ],
      open_modal: true,
    }
  }
}
</script>

<style>

</style>
