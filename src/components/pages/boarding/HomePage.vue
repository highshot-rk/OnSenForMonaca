<template>
  <div class="full-screen">
      <div class="back-image">

      </div>
      <div class="blue-screen">

      </div>
      <div class="title">
          Swim Lab
      </div>
  </div>
</template>

<script>

export default {
    name: "HomePage",
}
</script>

<style lang="css" scoped>
    .full-screen {
        width: 100vw;
        height: 100vh;
        position: relative;
    }
    .back-image {
        width: 100vw;
        height: 100vh;
        background: url("../../../assets/images/v292_6962.png");
        background-repeat: no-repeat;
        background-position: center center;
        background-attachment: fixed;
        /* background-size: cover; */
        opacity: 1;
        position: relative;
        top: 0px;
        left: 0px;
        overflow: hidden;
    }
    .blue-screen {
        position: absolute;
        background-color: rgb(0, 0, 248);
        opacity: 0.8;
        width: 100vw;
        height: 100vh;
        top: 0;
        left: 0px;
    }
    .title {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        color: white;
        font-size: 40px;
    }
</style>
