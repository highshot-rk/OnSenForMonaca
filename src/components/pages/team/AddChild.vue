<template>
  <v-ons-page>
    <div>
        <child-photo></child-photo>
    </div>
  </v-ons-page>
</template>

<script>
import ChildPhoto from './component/ChildPhoto.vue';

export default {
    name: "addchild",
    components: {
        ChildPhoto
    },
}
</script>

<style scoped>

</style>
