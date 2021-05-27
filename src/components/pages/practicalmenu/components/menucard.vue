<template>
    <v-ons-card class="card-item">
        <div class="card-title">
            <span>メニュー #{{number}}</span>
        </div>
        <div class="card-sub-title">
            <v-ons-row class="item-row">
                <v-ons-col class="card-sub-title-1" width="25%">種類</v-ons-col>
                <v-ons-col class="card-sub-title-1" width="25%">種目</v-ons-col>
                <v-ons-col class="card-sub-title-1" width="25%">内容</v-ons-col>
                <v-ons-col class="card-sub-title-1" width="25%">強度</v-ons-col>
            </v-ons-row>
            <v-ons-row class="item-row">
                <v-ons-col class="card-sub-title-2" width="25%">Swim</v-ons-col>
                <v-ons-col class="card-sub-title-2" width="25%">Choice</v-ons-col>
                <v-ons-col class="card-sub-title-2" width="25%">Drill</v-ons-col>
                <v-ons-col class="card-sub-title-2" width="25%">EN1</v-ons-col>
            </v-ons-row>
        </div>
        <hr style="opacity: 0.2;">

        <v-ons-list>
            <v-ons-list-item expandable :expanded.sync="isCardTableExpanded">
                <div class="card-table expandable-content">
                    <v-ons-row class="item-row">
                        <v-ons-col class="item-header" width="20%">セット</v-ons-col>
                        <v-ons-col class="item-header" width="20%">距離</v-ons-col>
                        <v-ons-col class="item-header" width="20%">本数</v-ons-col>
                        <v-ons-col class="item-header" width="20%">サイクル</v-ons-col>
                        <v-ons-col class="item-header" width="20%">セット間</v-ons-col>
                    </v-ons-row>
                    <v-ons-row class="item-row" v-for="data, index in dataList" :key="index">
                        <v-ons-col class="item-content" width="20%">#{{index+1}}</v-ons-col>
                        <v-ons-col class="item-content" width="20%">{{data.distance}}</v-ons-col>
                        <v-ons-col class="item-content" width="20%">{{data.count}}</v-ons-col>
                        <v-ons-col class="item-content" width="20%">{{data.cycle}}</v-ons-col>
                        <v-ons-col class="item-content" width="20%">{{data.between_sets}}</v-ons-col>
                    </v-ons-row>
                    <hr style="opacity: 0.2;">
                </div>
                <div class="right" style="display: none"></div>
                <div class="top" style="display: none"></div>
            </v-ons-list-item>
        </v-ons-list>
        <div style="display: flex;">
          <v-ons-button @click="isCardTableExpanded = !isCardTableExpanded" modifier="quiet" class="card-bottom-text" style="margin-left: 1rem;display: flex; align-items: center; flex: 1 1 auto;">
              <v-ons-icon modifier="outline" size="30px" :icon="this.icon_status"/>セット数:{{dataList.length}}
          </v-ons-button>
          <template v-if="ready">
            <div style="display: flex; ">
              <v-ons-button
                style="border-radius: 100px;background: transparent;border: 2px solid #0089FF;color: #0089FF;font-size: 0.7rem;display: flex; align-items: center;height: 24px;margin-right: 10px;"
                @click="clickSkip()"
              >
                <span>スキップ</span>
              </v-ons-button>
              <v-ons-button
                style="border-radius: 100px;font-size: 0.7rem;display: flex; align-items: center;height: 24px;margin-right: 10px;"
                @click="clickStart()"
              >
                <span class="material-icons">play_arrow</span>
                <span>開始</span>
              </v-ons-button>
            </div>
          </template>
          <template v-if="done">
            <div style="display: flex; " @click="clickRedo()">
              <v-ons-button style="border-radius: 100px;font-size: 0.7rem;display: flex; align-items: center;height: 24px;margin-right: 10px;padding-left: 3rem; padding-right: 3rem;">
                <span>#2やり直す</span>
              </v-ons-button>
            </div>
          </template>
        </div>
    </v-ons-card>
</template>
<script>
export default {
    name: "menu-card",
    data: function() {
        return {
            // title: '練習メニュー一覧',
            isCardTableExpanded: false
        }
    },
    components: {
    },
    computed: {
        icon_status: function () {
            return this.isCardTableExpanded ? "md-chevron-up" : "md-chevron-down";
        }
    },
    props: {
        "dataList": {
            type: Array,
            default: () => [
                {"distance": 30, "count": 4, "cycle": "1’0.", "between_sets": 0},
                {"distance": 50, "count": 2, "cycle": "1’0.", "between_sets": 2},
                {"distance": 20, "count": 3, "cycle": "1’0.", "between_sets": 1},
                {"distance": 50, "count": 5, "cycle": "1’0.", "between_sets": 3},
                {"distance": 60, "count": 1, "cycle": "1’0.", "between_sets": 1},
            ]
        },
        "number": {
            type: Number,
        },
        "totalTime": {
            type: String,
            default: "2h 45m"
        },
        "ready": true,
        "done": false,
    },
    methods: {
      clickStart() {
        this.$emit('start-practice');
      },
      clickSkip() {
        this.$emit('skip-practice');
      },
      clickRedo() {
        this.$emit('redo-practice');
      }
    }
}
</script>

<style scoped>
    .card-item {
        margin: 1.5rem 0 0.2rem 0;
        text-align: center;
        align-items: center;
        padding: 1rem 0 0.7rem 0;
    }
    .card-title {
        margin-left: 1rem;
        font-family: "SF Pro Text";
        font-style: normal;
        font-weight: bold;
        font-size: 16px;
        line-height: 150%;
        color: #303235;
        text-align: left;
    }
    .card-sub-title {
        margin: 0.5rem;
        padding: 0.2rem 0;
        background: #F1F7FC;
        border-radius: 4px;
    }
    .card-sub-title-1 {
        font-family: "Noto Sans JP";
        font-style: normal;
        font-weight: normal;
        font-size: 12px;
        line-height: 150%;
        text-align: center;
        color: #8293A3;
    }
    .card-sub-title-2 {
        font-family: "SF Pro Display";
        font-style: normal;
        font-weight: normal;
        font-size: 14px;
        line-height: 17px;
        text-align: center;
        color: #5496D7;
    }
    .card-table {
        margin: 0.5rem;
    }
    .item-header {
        font-family: "Noto Sans JP";
        font-style: normal;
        font-weight: normal;
        font-size: 12px;
        line-height: 150%;
        text-align: center;
        color: #8293A3;

    }
    .item-row {
        margin: 0.2rem 0;
    }
    .item-content {
        padding: 0.3rem 0;
        font-family: "SF Pro Display";
        font-style: normal;
        font-weight: bold;
        font-size: 14px;
        line-height: 17px;
        text-align: center;
        color: #5496D7;
        background: #F1F7FC;
        box-shadow: inset -0.5px 0px 0px rgba(84, 150, 215, 0.5);
    }
    .card-bottom-text {
        margin: 0;
        padding: 0;
        text-align: left;
        color: #0089FF;
        vertical-align: center;
        font-family: "SF Pro Display";
        font-style: normal;
        font-weight: normal;
        font-size: 16px;
        line-height: 150%;
    }
</style>
