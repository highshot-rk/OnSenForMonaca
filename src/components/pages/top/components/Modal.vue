<template>
  <div class="modal" :style="modalStyle">
    <div class="container">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'modal',
  props: [
    "open"
  ],
  computed: {
    modalStyle() {
      return {
        display: this.open ? "block" : "none"
      }
    }
  },
  methods: {
    closeModal() {
      if (this.open) {
        this.$emit("close-modal");
      }
    }
  }
}
</script>

<style scoped>
  .modal {
    position: fixed;
    padding: 8rem 0.5rem;
    width: 100vw;
    height: 100vh;
    background-color: #33333377;
  }
  .modal .container {
    padding: 2rem 1.5rem;
    background-color: white;
    border-radius: 1rem;
    min-height: 60vh;
  }
</style>
