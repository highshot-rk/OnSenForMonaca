<template>
    <div class="borading-1">
        <page-header-round>
            <p class="title"><span style="font-weight: bold">Swim Lab</span> へようこそ！</p>
        </page-header-round>
        <div class="content">
            <p class="description">
                SwimLabはあなた専用のアシスタントコーチです。私がどのようなお手伝いができるか、紹介させてください。
            </p>
            <boarding-mode-block />
        </div>
    </div>
</template>

<script>
import PageHeaderRound from './component/PageHeaderRound';
import BoardingModeBlock from './component/BoardingModeBlock';

export default {
    name: "boarding",
    components: {
        PageHeaderRound,
        BoardingModeBlock,
    },
}
</script>

<style scoped>
    p.title {
        position: absolute;
        top: 10vh;
        font-size: 1.5rem;
        text-align: left;
        left: 2rem;
        color: white;
        width: fit-content;
    }
    div.content {
        padding: 2rem;
    }
    p.description {
        text-align: left;
        font-size: 1.1rem;
        color: gray-dark;
    }
</style>
