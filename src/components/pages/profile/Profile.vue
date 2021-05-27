<template>
  <v-ons-page>
    <div>
        <!-- <ProfileNavigator></ProfileNavigator> -->
        <Photo></Photo>
    </div>
  </v-ons-page>
</template>

<script>
//import ProfileNavigator from './component/ProfileNavigator';
import Photo from "./component/Photo";

export default {
    name: "profile",
    components: {
        //ProfileNavigator
        Photo
    },
}
</script>

<style scoped>

</style>
