<template>
  <v-ons-page>
    <v-ons-toolbar class="header">
        <div class="left"><v-ons-back-button modifier="quiet" class=" h_left"><span class="material-icons">close</span></v-ons-back-button></div>
        <div class="center"><span class="h_title">練習タイム検索条件</span></div>
        <div class="right"><v-ons-button modifier="quiet" class=" h_right"><span class="right-title">クリア</span></v-ons-button></div>
    </v-ons-toolbar>
    <div class="add_content">
      <div class="ac_title"><span>練習実施日</span></div>
      <div class="ac_calendar1">
        <input class="grey_btn width-164" type="date">
        <input class="grey_btn width-164" type="date">
      </div>
      <div class="ac_title mt-24"><span>種目</span></div>
      <div class="ac_calendar">
        <select class="grey_btn"
            v-model="selectedRaceType1"
          >
            <option v-for="raceType in raceTypes" :value="raceType" :key="raceType.id">
              {{ raceType }}
            </option>
          </select>
      </div>
      <div class="ac_title mt-24"><span>内容</span></div>
      <div class="ac_calendar">
        <select class="grey_btn"
            v-model="selectedRaceType2"
          >
            <option v-for="raceType in raceTypes" :value="raceType" :key="raceType.id">
              {{ raceType }}
            </option>
          </select>
      </div>
      <div class="ac_title mt-24"><span>種類</span></div>
      <div class="ac_calendar">
        <select class="grey_btn"
            v-model="selectedRaceType3"
          >
            <option v-for="raceType in raceTypes" :value="raceType" :key="raceType.id">
              {{ raceType }}
            </option>
          </select>
      </div>
      <div class="ac_title mt-24"><span>強度</span></div>
      <div class="ac_calendar">
        <select class="grey_btn"
            v-model="selectedRaceType4"
          >
            <option v-for="raceType in raceTypes" :value="raceType" :key="raceType.id">
              {{ raceType }}
            </option>
          </select>
      </div>
      <div class="ac_title mt-24"><span>距離</span></div>
      <div class="ac_calendar">
        <select class="grey_btn"
            v-model="selectedRaceType5"
          >
            <option v-for="raceType in raceTypes" :value="raceType" :key="raceType.id">
              {{ raceType }}
            </option>
          </select>
      </div>
      <div class="b_btn"><v-ons-button class="b_btn_bt" @click="checkPro"><span class="b_btn_cap">検索</span></v-ons-button></div>
      <v-ons-alert-dialog modifier="rowfooter"
        :visible.sync="checkProFlag"
      >
        <span slot="title" class="m_title">Proスイマー登録が必要です</span>
        <p class="m_content">1ヶ月以上前のデータを閲覧するにはProスイマー登録が必要です</p>
        <template slot="footer" class="m_btn">
          <v-ons-alert-dialog-button @click="checkProFlag = false">キャンセル</v-ons-alert-dialog-button>
          <v-ons-alert-dialog-button @click="goResults">確認する</v-ons-alert-dialog-button>
        </template>
      </v-ons-alert-dialog>
    </div>
  </v-ons-page>
</template>

<script>
  import PracticeSearchResult from './component/PracticeSearchResult';
  export default {
    name: 'practicesearch',
    data(){
      return {
        checkProFlag: false,
        selectedRaceType1: '指定なし',
        selectedRaceType2: '指定なし',
        selectedRaceType3: '指定なし',
        selectedRaceType4: '指定なし',
        selectedRaceType5: '指定なし',
        raceTypes: ['指定なし', '指定なし1', '指定なし2'],
      }
    },
    methods:{
      checkPro(){
        this.checkProFlag = true;
      },
      goResults(){
        this.checkProFlag = false
        this.push_screen.push(PracticeSearchResult);
      }
    }
  }
</script>

<style scoped>
  .m_btn{
    font-family: "SF Pro Text";
    font-style: normal;
    font-weight: normal;
    font-size: 17px;
    line-height: 22px;
    text-align: center;
    letter-spacing: -0.408px;
    color: #007AFF;
  }
  .m_content{
    font-family: "SF Pro Text";
    font-style: normal;
    font-weight: normal;
    font-size: 13px;
    line-height: 16px;
    text-align: center;
    flex: none;
    letter-spacing: -0.078px;
    color: #000000;
  }
  .m_title{
    font-family: "SF Pro Text";
    font-style: normal;
    font-weight: 600;
    font-size: 17px;
    line-height: 22px;
    text-align: center;
    letter-spacing: -0.408px;
    color: #000000;
  }

  .width-164{
    width: 140px !important;
  }
  .ac_title{
    font-family: "Noto Sans CJK JP";
    font-style: normal;
    font-weight: bold;
    font-size: 12px;
    line-height: 150%;
    margin-left: 19px;
    display: flex;
    align-items: center;
    text-align: center;
    color: #193342;
  }
  .mt-24{
    margin-top: 24px;
  }
  .ac_calendar{
    display: flex;
    justify-content: center;
  }
  .ac_calendar1{
    display: flex;
    justify-content: space-evenly;
  }
  .grey_btn{
    background: rgba(0, 0, 0, 0.05);
    border-radius: 34px;
    padding: 12px 15px;
    width: 340px;
    margin-top: 8px;
    border-width: 0px;
    font-family: "Noto Sans CJK JP";
    font-style: normal;
    font-weight: normal;
    font-size: 14px;
    line-height: 150%;
    color: #707070;
  }
  .add_content{
    margin-top:70px;
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
  .right-title{
    font-family: "Noto Sans JP";
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 150%;
    color: #0089FF;
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
      font-family: "Noto Sans CJK JP";
      font-style: normal;
      font-weight: bold;
      font-size: 16px;
      line-height: 150%;
      color: #FFFFFF;
  }
  .b_btn{
    margin-top: 48px;
    display: flex;
    justify-content: center;
  }
  .b_btn_bt{
    width: 84.5vw;
    padding: 16px 96px;
    background: #0089FF;
    border-radius: 30px;
  }
</style>
