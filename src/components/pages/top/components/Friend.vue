<template>
  <div>
    <img :src="imgUrl" alt="" />
    <p class="name">{{name}}</p>
    <p class="data" :style="{color: dataColor}">{{data}}</p>
  </div>
</template>

<script>
export default {
  name: 'friend',
  props: [
    "imgUrl",
    "name",
    "data",
    "dataColor",
  ],
  mounted () {
    console.log("ASD")
  }
}
</script>

<style scoped>
  img {
    border-radius: 100px;
  }
  p.name {
     text-align: center;
     margin-top: -1rem;
     margin-bottom: 0px;
     font-weight: 400;
  }
  p.data {
     text-align: center;
     margin: 0rem;
  }
</style>
