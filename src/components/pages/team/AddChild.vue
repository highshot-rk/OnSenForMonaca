<template>
  <v-ons-page>
    <div>
        <ChildPhoto></ChildPhoto>
    </div>
  </v-ons-page>
</template>

<script>
import ChildPhoto from "./component/ChildPhoto";

export default {
    name: "addchild",
    components: {
        ChildPhoto
    },
}
</script>

<style scoped>

</style>
