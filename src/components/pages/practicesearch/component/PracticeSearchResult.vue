<template>
  <v-ons-page>
    <v-ons-toolbar class="header">
        <div class="left"><v-ons-back-button modifier="quiet" class=" h_left"><span class="material-icons">close</span></v-ons-back-button></div>
        <div class="center"><span class="h_title">練習タイム検索結果</span></div>
        <div class="right"><v-ons-button modifier="quiet" class=" h_right"><span class="material-icons">tune</span></v-ons-button></div>
    </v-ons-toolbar>
    <div class="category">
      <v-ons-carousel swipeable overscrollable style="padding: 0; margin-left:14px" item-width="35%" auto-refresh="true"
      >
        <v-ons-carousel-item v-for="(value, key) in categories" :key="key">
          <label class="cat_item">{{value}}</label>
        </v-ons-carousel-item>
      </v-ons-carousel>
    </div>
    <div class="results">
      <v-ons-card style="margin:0px">
        <div class="main_title">
          <v-ons-row >
            <v-ons-col width="40%" style="text-align: center;"><span class="mt_title">記録日</span></v-ons-col>
            <v-ons-col width="30%" style="text-align: center;"><span class="mt_title">距離</span></v-ons-col>
            <v-ons-col width="30%" style="text-align: center;"><span class="mt_title">ランキングタイム</span></v-ons-col>
          </v-ons-row>
          <v-ons-row>
            <v-ons-col width="40%" style="text-align: center;"><span class="mt_content">{{search_title[0]}}</span></v-ons-col>
            <v-ons-col width="30%" style="text-align: center;" class="mt_content"><span>{{search_title[1]}}</span></v-ons-col>
            <v-ons-col width="30%" style="text-align: center;" class="mt_content"><span>{{search_title[2]}}</span></v-ons-col>
          </v-ons-row>
        </div>
        <hr/>
        <div class="search_results">
          <div style="background: rgba(84, 150, 215, 0.08); padding: 4px">
            <v-ons-row >
              <v-ons-col width="25%" style="text-align: center;"><span class="mt_title">種類</span></v-ons-col>
              <v-ons-col width="25%" style="text-align: center;"><span class="mt_title">種目</span></v-ons-col>
              <v-ons-col width="25%" style="text-align: center;"><span class="mt_title">内容</span></v-ons-col>
              <v-ons-col width="25%" style="text-align: center;"><span class="mt_title">強度</span></v-ons-col>
            </v-ons-row>
            <v-ons-row>
              <v-ons-col v-for="cat in search_cat" :key='cat' width="25%" style="text-align: center;"><span class="ms_result">{{cat}}</span></v-ons-col>
            </v-ons-row>
          </div>

          <div v-for="menu, index in search_menu" :key="index" style="background: rgba(84, 150, 215, 0.08); margin:10px; padding: 4px">
            <v-ons-row >
              <v-ons-col width="25%" style="text-align: center;"><span class="mt_title">メニュー</span></v-ons-col>
              <v-ons-col width="25%" style="text-align: center;"><span class="mt_title">セット</span></v-ons-col>
              <v-ons-col width="25%" style="text-align: center;"><span class="mt_title">本数</span></v-ons-col>
            </v-ons-row>
            <v-ons-row>
              <v-ons-col width="25%" style="text-align: center;"><span class="ms_result">{{menu.menu}}</span></v-ons-col>
              <v-ons-col width="25%" style="text-align: center;"><span class="ms_result">{{menu.set}}</span></v-ons-col>
              <v-ons-col width="25%" style="text-align: center;"><span class="ms_result">{{menu.count}}</span></v-ons-col>
              <v-ons-col width="25%" style="text-align: center;">
                <v-ons-button modifier="quiet" style="margin-top: -20px"><span class="details">詳細 »</span></v-ons-button>
              </v-ons-col>
            </v-ons-row>
          </div>

        </div>
      </v-ons-card>
    </div>
  </v-ons-page>
</template>

<script>
  export default {
    name: "practicesearchresult",
    data(){
      return {
        categories: ["2月3日-3月17日", "Choice", "Drill", "EN1", "5 セット"],
        search_title: ['2021.03.17 月', '50m', '28.26'],
        search_cat: ['Swim', 'Choice', 'Drill', 'EN1'],
        sm_title: ['メニュー', 'セット', '本数'],
        search_menu:[{
          menu: '#6', set: '1セット目', count: '3本'
        }, {
          menu: '#6', set: '1セット目', count: '3本'
        }, {
          menu: '#6', set: '1セット目', count: '3本'
        }]
      }
    }
  }
</script>

<style scoped>
  .details{
    font-family: "SF Pro Display";
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 150%;
    color: #0089FF;
  }
  .ms_result{
    font-family: "SF Pro Display";
    font-style: normal;
    font-weight: normal;
    font-size: 14px;
    text-align: center;
    color: #5496D7;
  }
  hr {
    border-top: 1px solid lightgrey;
    width: 100vw;
    margin-left: -16px;
  }
  .mt_content{
    font-family: "SF Pro Display";
    font-style: normal;
    font-weight: bold;
    font-size: 16px;
    line-height: 150%;
    color: #303235;
  }
  .mt_title{
    font-family: "SF Pro Display";
    font-style: normal;
    font-weight: normal;
    font-size: 12px;
    line-height: 150%;
    color: #8293A3;
  }
  .main_title{
    margin-top: 17px;
  }
  .cat_item{
    font-family: "SF Pro Text";
    font-style: normal;
    font-weight: 500;
    font-size: 12px;
    line-height: 150%;
    color: #8293A3;
    background: rgba(130, 147, 163, 0.2);
    border-radius: 40px;
    padding: 4px 8px;
  }
  .category{
    margin-top: 88px;
    margin-bottom: 20px;
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
</style>
