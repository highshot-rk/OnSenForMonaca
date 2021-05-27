<template>
    <div>
        <h3 class="left">あなたは：</h3>
        <div class="wide">
            <div class="container">
                <div>
                    <div
                        class="block young"
                        v-bind:class="{ active: active == 1 }"
                        @click="activeTag(1)"
                    >
                        <img src="../../../../assets/images/young-user-group.png"/>
                        <p style="margin-bottom: 0px">コーチ</p>
                    </div>
                </div>
                <div>
                    <div
                        class="block old"
                        v-bind:class="{ active: active == 2 }"
                        @click="activeTag(2)"
                    >
                        <img src="../../../../assets/images/old-user-group.png"/>
                        <p style="margin-bottom: 0px">選手</p>
                    </div>
                </div>
                <div>
                    <div
                        class="block middle"
                        v-bind:class="{ active: active == 3 }"
                        @click="activeTag(3)"
                    >
                        <img src="../../../../assets/images/middle-user-group.png"/>
                        <p style="margin-bottom: 0px">サポーター</p>
                    </div>
                </div>
            </div>
            <p class="description">{{ greeting[active - 1] }}</p>
        </div>
        <v-ons-button
            modifier="large"
            class="confirm-button"
        >次へ</v-ons-button>
    </div>
</template>

<script>
export default {
    name: 'boarding-mode-block',
    data: function() {
        return {
            active: 1,
            greeting: [
                "指導以外は全て、私にお任せください。",
                "あなたの成長をデータで証明します。",
                "お子様の成長がひと目でわかります。"
            ]
        }
    },
    methods: {
        activeTag: function (event) {
            this.active = event
        }
    }
}
</script>

<style scoped>
    h3.left {
        text-align: left;
    }
    div.wide {
        margin-left: -1rem;
        margin-right: -1rem;
        margin-bottom: 3rem;
    }
    div.container {
        display: flex;
        justify-content: space-between;
    }
    div.block {
        padding: 10px;
        border: 1px solid rgb(32, 151, 255);
        border-radius: 5px;
    }
    div.block.active {
        background-color: rgb(204,231,255);
    }
    div.block p {
        color: rgb(84, 150, 215);
    }
    div.block.active p {
        font-weight: bold;
    }
    p.description {
        border-radius: 5px;
        background-color: rgb(230, 244, 255);
        padding-left: 1.5rem;
        padding-right: 1.5rem;
        padding-top: 1rem;
        padding-bottom: 1rem;
        color: rgb(0, 136, 255);
        font-weight: bold;
    }
    .confirm-button {
        border-radius: 100px;
        background-color: rgb(0, 136, 255);
        color: white;
    }
</style>
