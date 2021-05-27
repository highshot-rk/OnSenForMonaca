<template>
  <div class="head-card" style="border-radius: 10px;border-width: 1px; border-style: solid;" :style="{'border-color': color,background: color}">
    <p>{{title}}</p>
    <div
      class="content"
      style="background: white;border-bottom-right-radius: 10px;border-bottom-left-radius: 10px;"
    >
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'head-card',
  props: [
    "color",
    'title',
  ]
}
</script>

<style scoped>
  p {
    margin: 10px;
    color: white;
    text-align: center;
  }
  .head-card {
    margin: 0px;
    margin-top: 10px;
  }
  .head-card .content {
    padding: 10px;
  }
</style>
