<template>
    <div>
        <!-- <top-status-bar></top-status-bar> -->
        <l-side-bar></l-side-bar>
        <div class="main-container">
            <slot></slot>
        </div>
        <bottom-bar />
    </div>
</template>

<script>
import LSideBar from "./LSideBar";
import TopStatusBar from './TopStatusBar';
import BottomBar from '../components/BottomBar';
export default {
    components: {
        LSideBar,
        TopStatusBar,
        BottomBar
    }
}
</script>

<style scoped>
    .main-container {
        position: relative;
    }
</style>
