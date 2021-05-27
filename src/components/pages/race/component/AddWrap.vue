<template>
  <div class="main">
    <div>
      <p class="header"><span>レース #{{no}}</span>
      <v-ons-button modifier="quiet" class="m--10" @click="removeWrap">
        <span class="material-icons" style="color:#303235;">cancel</span>
      </v-ons-button>
      </p>
    </div>
    <div class="content">
      <div class="c_cat_title title_font">
        <span style='margin-left:14px'>種目</span><span style="margin-right: 107px">距離</span>
      </div>
      <div class="c_cat_content">
        <v-ons-select class="grey_btn w-170"
            v-model="cat_titles[0]"
          >
            <option v-for="cat_title in cat_titles" :value="cat_title" :key="cat_title.id">
              {{ cat_title }}
            </option>
          </v-ons-select>
          <v-ons-select class="grey_btn w-80"
            v-model="cat_lengths[0]"
          >
            <option v-for="cat_length in cat_lengths" :value="cat_length" :key="cat_length.id">
              {{ cat_length }}m
            </option>
          </v-ons-select>
      </div>
      <div class="c_rest_time_title title_font">
        <span>レースタイム (全体）</span>
      </div>
      <div class="c_rest_time_content ml-25" style="margin-left: -25%">
        <wrap-time :closeBtn="false"></wrap-time>
      </div>
      <div class="c_wrap_title title_font">
        <span>ラップタイム</span>
      </div>
      <div class="ml-40" style="margin-left: 0px">
          <wrap-time v-for="(curTime, index) in currentTimeData" :key='index' :closeBtn="true" :no="index + 1" @removeTime="removeTime($event)"></wrap-time>
      </div>
      <div class="add_wrap">
        <div class="center mt-16">
        <v-ons-button modifier="quiet" class=" abt_top-32" @click="addTime"><span class="material-icons ml-30">add</span><span class="ml-21">ラップを追加</span></v-ons-button>
      </div>
      </div>
    </div>
    <div class="bottom"></div>
  </div>
</template>

<script>
import WrapTime from './WrapTime.vue'
  export default {
  components: { WrapTime },
    name: 'addwrap',
    props: ['wrapData', 'no'],
    data(){
      return{
        currentTimeData: this.wrapData.time_cate,
        cat_titles: ['自由形', '自由形1', '自由形2'],
        cat_lengths: [200, 100, 300],
      }
    },
    methods: {
      removeTime(id){
        this.currentTimeData.splice(id - 1, 1);
      },
      addTime(){
        this.currentTimeData.push({min: 0, second: 0, mili: 0});
      },
      removeWrap(){
        this.$emit('removeWrap', this.no);
      }
    }
  }
</script>

<style scoped>
  .ml-21{
    vertical-align: super;
    margin-left: 21px;
    font-family: "Noto Sans JP";
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 150%;
    color: #0089FF;
  }
  .add_wrap{
    margin-top: 16px;
    margin-bottom: 24px;
    margin-left: 0px;
  }
  .ml-40{
    margin-left: 15%;
  }
  .ml-25{
    margin-left: 3%;
  }
  .c_rest_time_content{
    display: flex;
    justify-content: center;
  }
  .c_cat_title{
    display: flex;
    justify-content: space-between;
  }
  .c_cat_content{
    display: flex;
    justify-content: space-evenly;
  }
  .w-170{
    width: 170px;
  }
  .w-80{
    width: 80px;
  }
  .grey_btn{
    background: white;
    border-radius: 34px;
    padding: 8px 12px;
    margin-top: 8px;
    font-family: "SF Pro Display";
    font-size: 16px;
    line-height: 150%;
    color: #303235;
  }
  .title_font{
    font-family: "Noto Sans CJK JP";
    font-style: normal;
    font-weight: bold;
    font-size: 12px;
    line-height: 150%;
    color: #193342;
    margin-left: 16px;
    margin-top: 24px;
  }
  .m--10{
    margin: -10px;
  }
  .header{
    font-family: "Noto Sans CJK JP";
    font-weight: bold;
    font-size: 12px;
    padding-top: 16px;
    padding-left: 16px;
    padding-right: 16px;
    color: #0089FF;
    display: flex;
    justify-content: space-between;
  }
  .main{
    margin-top: 24px;
    background: rgba(84, 250, 215, 0.12);
    border-radius: 8px;
  }

</style>
