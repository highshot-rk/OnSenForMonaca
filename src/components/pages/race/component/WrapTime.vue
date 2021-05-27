<template>
  <div class="c_wrap_content">
    <span v-if="no" class="center1 mr-10">#{{no}}</span>
    <v-ons-input class="grey_btn w-50" type="number" min='0'></v-ons-input>
    <span class="mlr-10 center">分</span>
    <v-ons-input class="grey_btn w-50" type="number" min='0' ></v-ons-input>
    <span class="mlr-10 center">秒</span>
    <v-ons-input class="grey_btn w-50" type="number" min='0' ></v-ons-input>
    <v-ons-button modifier="quiet" class="ml-30" v-if="closeBtn" @click="removeSelf">
      <span class="material-icons" style="color:#303235; background:#D3D3D3; border-radius: 50%;padding:3px; font-size:16px">close</span>
    </v-ons-button>
  </div>
</template>

<script>
  export default {
    name:'wraptime',
    props: ['closeBtn', 'no'],
    methods:{
      removeSelf(){
        this.$emit("removeTime", this.no);
      }
    }
  }
</script>

<style scoped>
  .c_wrap_content{
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .mr-10{
    margin-right: 10px;
  }
  .ml-30{
    margin-left: 30px;
    margin-top: 10px;
  }
  .center1{
    font-family: "SF Pro Text";
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 150%;
  }
  .center{
    align-self: center;
    font-family: "Noto Sans CJK JP";
    font-style: normal;
    font-weight: normal;
    font-size: 14px;
    line-height: 21px;
    color: #707070;
  }
  .mlr-10{
    margin: 0px 4px 0px 4px;
  }
  .w-50{
    width: 40px;
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
</style>
