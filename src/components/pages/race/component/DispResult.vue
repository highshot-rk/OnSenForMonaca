<template>
  <div>
    <div class="header">
      <div class="title">
        <span>{{name}}</span>
        <v-ons-button modifier="quiet" class="right" @click="edit_reace()"><span class="material-icons">edit</span></v-ons-button>
      </div>
      <div class="time">
        <p>{{time}}</p>
      </div>
    </div>
    <div class="content">
      <div v-for="item in data" :key='item.id' class="sub_content">
        <div class="cat_title">
          <span class="ct_title">{{item.title}}</span>
          <span class="right mr_18">{{item.time}}</span>
          <span v-if="item.star" class="right material-icons yellow mr-8 size-8 mt-8">star</span>
        </div>
        <div class="cat_info">
          <p class="mr_18 font_12">{{item.subTitle}}</p>
        </div>
      </div>
    </div>
  </div>

</template>

<script>
  import AddRace from './AddRace';
  export default {
    name: 'DispResult',
    props: ['name', 'time', 'data'],
    methods:{
      edit_reace(){
        this.$emit("editRace", {
          extends: AddRace,
          data(){
            return {
              edit_id: 100, // this value is id to edit Race.
            }
          }
        })
        // this.push_screen.push(AddRace);
      }
    }
  }
</script>

<style scoped>

  .size-8{
    font-size: 16px;
  }
  .yellow{
    color:#E9A904;
  }
  .mt-8{
    margin-top: 4px;
  }
  .mr-8{
    margin-right: 8px;
  }
  .font_12{
    font-size: 12px !important;
    font-weight: normal !important;
    color:#707070 !important;
    margin-top: 4px;
  }
  .mr_18{
    margin-right: 18px;
    font-family: "SF Pro Display";
    font-style: normal;
    font-weight: bold;
    font-size: 16px;
    line-height: 150%;
    text-align: right;
    color: #303235;
  }
  .right{
    float: right;
  }
  .ct_title{
    font-family: "SF Pro Display";
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 150%;
    color: #8293A3;
    margin-left: 25px;
  }
  .cat_title{
    margin-top: 8px;
  }
  .title{
    margin-top: 24px;
  }
  .time{
    border-bottom: 1px solid lightgrey;
  }
  .content{
    border-bottom: 1px solid lightgrey;
  }
  .sub_content{
    border-bottom: 1px solid lightgrey;
  }
  .time>p{
    font-size: 10px;
    color: #707070;
    margin-left: 25px;
    margin-bottom: 16px;
  }
  .title>span{
    font-family: "SF Pro Display";
    font-style: normal;
    font-weight: bold;
    font-size: 20px;
    line-height: 150%;
    margin-left: 25px;
  }
</style>
