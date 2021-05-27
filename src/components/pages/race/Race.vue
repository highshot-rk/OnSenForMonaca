<template>
  <v-ons-page>
    <v-ons-toolbar class="header">
        <div class="left"><v-ons-back-button modifier="quiet" class=" h_left"><span class="material-icons">west</span></v-ons-back-button></div>
        <div class="center"><span class="h_title">大会の結果</span></div>
        <div class="right"><v-ons-button modifier="quiet" class=" h_right"><span class="material-icons">add</span></v-ons-button></div>
    </v-ons-toolbar>
    <div>
      <div class="content">
        <div v-for="info in resultData" :key="info.id">
          <Info :name="info.name" :time='info.time' :data='info.categoryData' @editRace="editRace($event)"></Info>
        </div>
      </div>
    </div>
    <div class="addBtn">
      <v-ons-button modifier="quiet" class=" abt_top-32"  @click="add_race"><span class="material-icons ml-30">add</span><span class="ml-21">レース結果を追加</span></v-ons-button>
    </div>
    <v-ons-bottom-toolbar class="tool_bottom">
      <div class="tab-bottom">
        <div style="text-align: center">
          <v-ons-button modifier="quiet">
          <span style="width: 18px; height: 18px; margin: 3px;" class='material-icons'>event_note</span>
          <p style="margin: -10px; font-weight: bold;font-size: 10px;">サマリー</p>
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
  import Info from './component/DispResult';
  import AddRace from './component/AddRace';
  export default {
    name: 'race',
    components: {
      Info,
    },
    methods: {
      add_race(){
        this.push_screen.push(AddRace);
      },
      editRace(component){
        this.push_screen.push(component);
      }
    },
    data(){
      return {
        resultData: [
          {name: '全国大会', time: '2021.06.30', categoryData: [
            {title: 'バタフライ100m', time: '02:30', subTitle: 'ラップ：0:30, 0:30', star: false}, {title: '自由形100m', time: '02:30', subTitle: 'ラップ：0:30, 0:30', star: false}
          ]},
          {name: '全国大会2', time: '2021.06.30', categoryData: [
            {title: 'バタフライ100m', time: '02:30', subTitle: 'ラップ：0:30, 0:30', star: true}, {title: '自由形100m', time: '02:30', subTitle: 'ラップ：0:30, 0:30', star: false}
          ]}
        ]
      }
    }
  }
</script>

<style scoped>
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
  .ml-21{
    vertical-align: super;
    margin-left: 21px;
  }
  .ml-30{
    margin-left: 15px;
  }
  .abt_top-32{
    margin-top: 32px;
    font-family: "Noto Sans JP";
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 150%;
    color: #0089FF;
  }
  .top-54{
    margin-top: 40px;
  }
  .content{
    margin-top:70px;
  }
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

</style>
