<template>
  <v-ons-page>
    <div class="black">
      <div class="top">
        <div>
          <v-ons-back-button class="close_btn"><span class="material-icons">close</span></v-ons-back-button>
        </div>
      </div>
      <div><img src='static/images/lg_girl.png' class="img_size"></div>
      <div class="bottom">
        <v-ons-back-button class="b_apply"><span class="material-icons"><span class="b_apply_txt">写真を適用</span></span></v-ons-back-button>
      </div>
    </div>
  </v-ons-page>
</template>

<script>

export default {
    name: "camera",
}
</script>
<style scoped>
  .b_apply_txt{
    font-size: 16px;
    color: #FFFFFF;
  }
  .b_apply{
    font-family: "Noto Sans CJK JP";
    font-style: normal;
    font-weight: normal;
    float: right;
    margin-right: 21px;
    margin-top: 70px;
  }
  .close_btn{
    color: white;
    margin-left: 0px;
    margin-top: 55px;
  }
  .bottom{
    height: 175px;
  }
  .top{
    height: 134px;
  }
  .black{
    background-color: black;
  }
  .img_size{
    width: 100%;
    height: 500px;
  }
</style>
