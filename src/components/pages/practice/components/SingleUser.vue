<template>
  <div>
      <div class="img-class" :style="{background: user.color}">
        <img :src="user.img" alt="">
      </div>
      <p></p>
  </div>
</template>

<script>
export default {
    name: 'single-user',
    props: [
        "user",
    ]
}
</script>

<style scoped>
    div {
        border-radius: 1000px;
        padding: 0.5rem;
    }
    img {
        width: 1.8rem;
        height: 1.8rem;
    }
    p {
        width: 2rem;
        height: 1rem;
        background: #E7E7E7;
        margin: auto;
        margin-top: 1rem;
        border-radius: 3px;
    }
</style>