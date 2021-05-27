<template>
  <div class="primary">
      <slot></slot>
  </div>
</template>

<script>
export default {
    name: 'focus-text'
}
</script>

<style scoped>
    .primary {
        background: #29B9E7;
        padding: 4px;
        color: white;
        width: fit-content;
        border-radius: 3px;
        font-size: 0.7rem;
        margin: 0px;
    }
</style>
