<template>
  <v-ons-page>
    <v-ons-toolbar class="header">
        <div class="left"><v-ons-back-button modifier="quiet" class=" h_left"><span class="material-icons">close</span></v-ons-back-button></div>
        <div class="center"><span class="h_title">大会の結果を追加</span></div>
    </v-ons-toolbar>
    <div class="add_content">
      <div class="ac_title"><span>レースの日付</span></div>
      <div class="ac_calendar">
        <v-ons-input class="grey_btn" type="date" min='2000/11/23' :value="currentDate"></v-ons-input>
      </div>
      <div class="ac_title mt-24"><span>大会名</span></div>
      <div class="ac_calendar">
        <v-ons-input class="grey_btn" placeholder="" v-model="currentName"></v-ons-input>
      </div>
      <div class="ac_title mt-24"><span>プール</span></div>
      <div class="ac_calendar">
        <v-ons-select class="grey_btn"
            v-model="selectedRaceType"
          >
            <option v-for="raceType in raceTypes" :value="raceType" :key="raceType.id">
              {{ raceType }}
            </option>
          </v-ons-select>
      </div>

    </div>
    <div class="add_wrap">
      <AddWrap v-for="(curWrap, index) in currentWrapData" :key='index' :no="index + 1" :wrapData = "curWrap" @removeWrap="removeWrap($event)"></AddWrap>
    </div>
    <div class="bottom">
      <div class="center mt-16">
        <v-ons-button modifier="quiet" class=" abt_top-32" @click="addRace"><span class="material-icons ml-30">add</span><span class="ml-21">レース結果を追加</span></v-ons-button>
      </div>
      <div class="b_btn">
        <v-ons-button class="b_btn_bt" @click="saveRace"><span class="b_btn_cap">保存</span></v-ons-button>
      </div>
    </div>
    <div class="removeRace">
      <v-ons-button v-if="edit_id !== -1" modifier="quiet" @click="showDelModal=true"><span class='del_btn'>この大会の結果を削除</span></v-ons-button>
    </div>
    <div class="del_confirm">
      <v-ons-alert-dialog modifier="rowfooter"
        :visible.sync="showDelModal"
      >
        <span slot="title" class="title">大会の結果を削除</span>
        <p class="content">本当にこの大会の結果を削除しますか？この操作は取り消せません。</p>
        <template slot="footer">
          <v-ons-alert-dialog-button @click="showDelModal = false"><span class="cancel">キャンセル</span></v-ons-alert-dialog-button>
          <v-ons-alert-dialog-button @click="deleteRace"><span class="ok">削除</span></v-ons-alert-dialog-button>
        </template>
      </v-ons-alert-dialog>
    </div>
  </v-ons-page>
</template>

<script>
  import AddWrap from './AddWrap';
  export default {
    name: 'addrace',
    components:{
      AddWrap,
    },
    data() {
      return {
        edit_id: -1,
        currentWrapData: [
          {
            time_main: {min: 0, second: 0, mili: 0},
            time_cate: [{min: 0, second: 0, mili: 0}, {min: 0, second: 0, mili: 0}]
          },
          {
            time_main: {min: 0, second: 0, mili: 0},
            time_cate: [{min: 0, second: 0, mili: 0}, {min: 0, second: 0, mili: 0}]
          },
        ],
        showDelModal: false,
        currentName: '全国大会',
        currentDate: new Date().toISOString().slice(0, 10),
        raceTypes: ['長水路', '長水路1', '長水路2'],
        selectedRaceType: '長水路'
      }
    },
  methods: {
    saveRace(){
      this.push_screen.pop();
    },
    removeWrap(id){
      this.currentWrapData.splice(id - 1, 1);
    },
    addRace(){
      this.currentWrapData.push({
        time_main: {min: 0, second: 0, mili: 0},
        time_cate: [{min: 0, second: 0, mili: 0}, {min: 0, second: 0, mili: 0}]
      })},
    deleteRace(){
      this.showDelModal = false;
      this.$ons.notification.toast('レースレコードを削除しました', {timeout: 2000, class: "text-alignL center"})
      this.push_screen.pop();
    }
  }
}
</script>

<style scoped>
  .center{
    text-align: center;
  }
  .content{
    font-family: "SF Pro Text";
    font-style: normal;
    font-weight: normal;
    font-size: 13px;
    line-height: 16px;
    text-align: center;
    letter-spacing: -0.078px;
    color: #000000;
    margin-left: 5px;
  }
  .title{
    font-family: "SF Pro Text";
    font-style: normal;
    font-weight: 600;
    font-size: 17px;
    line-height: 22px;
    text-align: center;
    letter-spacing: -0.408px;
    color: #000000;
  }
  .cancel{
    font-family: "SF Pro Text";
    font-style: normal;
    font-weight: normal;
    font-size: 17px;
    line-height: 22px;
    letter-spacing: -0.408px;
    color: #007AFF;
  }
  .ok{
    font-family: "SF Pro Text";
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 150%;
    align-items: center;
    text-align: center;
    color: #EA3223;
  }
  .del_btn{
    font-family: "Noto Sans JP";
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 150%;
    text-align: center;
    color: #EA3223;
  }
  .removeRace{
    display: flex;
    margin-top: 15px;
    margin-bottom: 80px;
    justify-content: center;
  }
  .add_wrap{
    margin-top: 24px;
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
    width: 320px;
    padding: 16px 96px;
    background: #0089FF;
    border-radius: 30px;
  }
  .ml-21{
    vertical-align: super;
    margin-left: 21px;
  }
  .center{
    display: flex;
    justify-content: center;
  }
  .mt-16{
    margin-top: 16px;
    font-family: "Noto Sans JP";
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 150%;
  }
  .mt-24{
    margin-top: 24px;
  }
  .ac_calendar{
    display: flex;
    justify-content: center;
  }
  .grey_btn{
    width: 135px;
    background: rgba(0, 0, 0, 0.05);
    border-radius: 34px;
    padding: 8px 15px;
    width: 300px;
    margin-top: 8px;
  }
  .add_content{
    margin-top:70px;
  }
  .ac_title{
    font-family: "Noto Sans CJK JP";
    font-style: normal;
    font-weight: bold;
    font-size: 12px;
    line-height: 150%;
    margin-left: 16px;
    display: flex;
    align-items: center;
    text-align: center;
    color: #193342;
  }
  .header{
    border-bottom: 1px solid lightgrey;
    height: 88px;
    padding-top: 40px;
  }
  .h_left{
    margin-left: 5px;
    margin-top: 5px;
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
