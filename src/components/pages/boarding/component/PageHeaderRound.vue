<template>
  <div class="page-header-round">
      <slot />
  </div>
</template>

<script>
export default {
    name: 'page-header-round'
}
</script>

<style scoped>
    .page-header-round {
        background: url("../../../../assets/images/boarding-top-round-image.png");
        background-size: cover;
        background-position: center;
        background-repeat: no-repeat;
        height: 30vh;
        width: 100vw;
    }
</style>
