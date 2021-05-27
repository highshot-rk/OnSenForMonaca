
<template>
    <v-ons-page>
        <v-ons-toolbar class="practice-toolbar">
            <div class="left">
                <v-ons-back-button>
                    <v-ons-icon modifier="outline" size="30px" icon="md-close, material:md-close-outline"></v-ons-icon>
                </v-ons-back-button>
            </div>
            <!-- </v-ons-col> -->
            <div class="center">
                <p class="toolbar-title">2021.03.17 練習メニュー</p>
            </div>
            <div class="right">
                <v-ons-toolbar-button>
                    <v-ons-icon modifier="outline" size="30px" icon="md-download, material:md-download-outline"></v-ons-icon>
                </v-ons-toolbar-button>
            </div>
        </v-ons-toolbar>
        <img src="../../../assets/images/practice_list.png" alt="" class="img-item" width="100%">
    </v-ons-page>
</template>

<script>
export default {
    name: "practice2",
    data: function() {
        return {

        }
    },
    components: {
    },
    props: {
    },
    computed: {
    },
    methods: {
    }
}
</script>

<style scoped>
    .practice-toolbar {
        margin: 0 0 0.5rem 0;
        padding: 3rem 0 0 0;
        text-align: center;
        align-items: center;
        border-radius: 0;
        background-color: white;
        height: 88px;
    }
    .toolbar-title {
        font-family: "Noto Sans JP";
        font-style: normal;
        font-weight: bold;
        font-size: 18px;
        color: #303235;
        margin-bottom: 0;
        height: 2.5rem;
    }
    .toolbar-sub-title {
        font-family: "SF Pro Display";
        font-style: normal;
        font-weight: normal;
        font-size: 11px;
        line-height: 13px;
        text-align: center;
        margin-top: 0;
        height: 2rem;
    }
    .card-item {
        text-align: center;
        margin: 0.2rem 0 0 0;
        width: 100%;
        padding: 0.5rem;
    }
    .img-item {
        margin: 1.5rem 0 0.5rem 0;
    }
</style>