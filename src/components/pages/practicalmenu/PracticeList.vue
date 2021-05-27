<template>
  <v-ons-page>
    <p class="page-title">練習メニュー一覧</p>
    <div style="padding: 0.8rem;">
      <v-ons-select v-model="selectedTeam" class="select-my" @change="selectTeam(selectedTeam)">
          <option v-for="(team, index) in teams" :value="team.value" :key="index">
          {{ team.text }}
          </option>
      </v-ons-select>
    </div>

    <template v-for="(card, index) in cardInfo">
      <v-ons-card :key="index" style="margin: 10px 0;padding: 1em;position: relative;">
        <div style="display: flex;align-items: center;">
          <p style="font-weight: bold;margin: 0;">{{card.date}}</p>
          <span style="margin-left: 10px" :style="{background: card.badgeColor}" class="badge">{{card.badge}}</span>
        </div>
        <div style="font-size: 0.8rem;color: #707070">
          <span>07:30 -</span>
          <span>ロンド成増</span>
        </div>
        <div style="font-size: 0.7rem;">
          <span style="color: #8293A3">総距離</span>
          <span style="margin-left: 0.5rem;">4,000m</span>
          <span style="color: #8293A3;margin-left: 1rem;">総時間</span>
          <span style="margin-left: 0.5rem;">2h45m</span>s
        </div>
        <div style="position: absolute;right: 10px; top: 15px;">
          <v-ons-button class="edit-btn">
            <span class="material-icons" style="font-size: 1rem;">
              content_copy
            </span>
            <span>練習を複製</span>
          </v-ons-button>
        </div>
        <div style="position: absolute;right: 10px; bottom: 15px;display:flex;">
          <img style="width: 24px;height: 24px;margin-right: -6px;" src="/static/assets/images/tempimg2.png" alt="">
          <img style="width: 24px;height: 24px;margin-right: -6px;" src="/static/assets/images/tempimg1.png" alt="">
          <img style="width: 24px;height: 24px;margin-right: -6px;" src="/static/assets/images/tempimg2.png" alt="">
          <img style="width: 24px;height: 24px;margin-right: -6px;" src="/static/assets/images/tempimg1.png" alt="">
          <div style="background: #707070;border-radius:100px;color:white;width: 24px; height: 24px;font-size: 0.8rem;display: flex;align-items: center;"><span>+12</span></div>
        </div>
      </v-ons-card>
    </template>

    <template v-if="this.openedBtn">
      <v-ons-button @click="toggleOpenedBtn()" style="border-radius: 100px;height: 3rem;width: 3rem;display: flex; align-items: center;position: absolute;right: 10px; bottom: 6rem;justify-content: center;font-weight: bold;">
        +
      </v-ons-button>
    </template>
    <template v-else>
      <v-ons-button @click="toggleOpenedBtn()" style="border-radius: 100px;height: 3rem;width: calc(100vw - 10rem);display: flex; align-items: center;position: absolute;bottom: 6rem;justify-content: center;margin: 0 5rem;font-weight: bold;">
        <span>+</span> <span style="padding-left: 10px;">新規メニュー</span>
      </v-ons-button>
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
  </v-ons-page>
</template>

<script>
export default {
  data() {
    return {
      teams: [
        {text: "Aチーム", value: 0},
        {text: "Bチーム", value: 1},
      ],
      selectedTeam: 0,
      cardInfo: [
        {date: "03.17 月", badge: "未実施", badgeColor: "#8293A3"},
        {date: "03.17 月", badge: "未実施", badgeColor: "#5496D7"},
        {date: "03.17 月", badge: "未実施", badgeColor: "#5496D7"},
        {date: "03.17 月", badge: "未実施", badgeColor: "#5496D7"},
        {date: "03.17 月", badge: "未実施", badgeColor: "#5496D7"},
      ],
      openedBtn: true,
    }
  },
  methods: {
    selectTeam(e) {

    },
    toggleOpenedBtn() {
      this.openedBtn = !this.openedBtn;
    }
  }
}
</script>

<style scoped>
  .page-title {
    font-weight: bold;
    text-align: center;
    background: white;
    margin: 0;
    padding: 0.5rem;
  }
  .badge {
    border-radius: 100px;
    padding: 5px;
    height: 1rem;
    font-size: 0.8rem;
    color: white;
  }
  .edit-btn {
    opacity: 0.9;
    background: transparent;
    border: 2px solid #5496D7;
    box-sizing: border-box;
    border-radius: 30px;
    color: #5496D7;
    font-weight: bold;
    padding: 0.2rem 0.5rem;
    font-size: 0.7rem;
    display: flex;
    align-items: center;
    height: 1.4rem;
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
