<template>
  <v-ons-navigator :page-stack="pageStack"  @push-page="pageStack.push($event)">
    <!-- <component :is="page" v-for="page in pageStack" :key="page.key" :page-stack="pageStack"></component> -->
  </v-ons-navigator>
</template>

<script>
  import MenuPage from './components/MenuPage'
  import Vue from 'vue';
  export default {
    data() {
      return {
        pageStack: [MenuPage]
      }
    },
    mounted(){
      Vue.prototype.push_screen = this.pageStack;
    },
  }
</script>
