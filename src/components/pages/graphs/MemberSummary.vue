<template>
  <div class="slide-page" style="height: 100vh; overflow: auto;">
    <l-side-bar
      :open="opened"
      @hide-sidebar="toggleLeftSideBar()"
    ></l-side-bar>
    <div :style="bodyStyle">
      <div style="background: lightgray;height: 2.5rem"></div>
      <div class="row" style="margin-top: -5px; background: white;padding-top: 1rem;border-top-left-radius: 0.5rem;border-top-right-radius: 0.5rem;">
        <img style="width: 1rem; height:1rem; margin-top: 1rem; margin-left: 1rem;" src="../../../assets/icons/Menu.png" alt=""  @click="toggleLeftSideBar()"/>
        <img style="width: 5rem; height: 5rem" src="../../../assets/images/student-girl.png" alt=""/>
        <div class="info">
            <p @click="dialogVisible = !dialogVisible" style="margin-top: 5px;display:flex; align-items: center;">
              <b>
                <template v-for="(item, index) in items" >
                  <span v-if="item.value" style="margin-left: 1rem" :key="index">{{item.key}}</span>
                </template>
              </b>
              <span class="material-icons">expand_more</span>
            </p>
            <p style="display: flex;margin-top: 5px;margin-bottom: 5px;"><focus-text>バタフライ 100m</focus-text><span style="margin-left: 5px;font-size: 0.7rem;    margin-top: 0.2rem;">ベスト : 1'07.48</span></p>
            <p style="display: flex;margin-top: 5px;margin-bottom: 5px;"><focus-text>自由形 100m</focus-text><span style="margin-left: 5px;font-size: 0.7rem;margin-top: 0.2rem;">ベスト : 1'03.82</span></p>
        </div>
      </div>
      <hr style="border-color: #41618011"/>
      <div class="row" style="padding: 0rem 1.2rem; display: flex; flex-direction: column;margin-bottom: 1rem;">
        <p style="display: flex;font-size: 1rem;color: black; margin-bottom: 15px;">練習</p>
        <div style="padding: 0;overflow: hidden;margin: 0;position: relative;border-radius: 10px;">
          <img style="border-radius: 10px;width:100%; height: auto;" src="static/assets/images/practice01.png" alt="">
          <p style="position: absolute; top: 0.2rem; left: 1rem;color: white;font-size: 1.5rem;font-weight: bold;">03.17 月</p>
          <p style="position: absolute; top: 2.8rem; left: 1rem;color: white;font-size: 0.8rem;">2021</p>
          <p style="position: absolute; top: 5rem; left: 1rem;color: white;font-size: 0.8rem;">練習開始まで 00:05:45</p>
        </div>
      </div>

      <div class="row" style="background: url('/static/assets/images/blue-water-bg.png'); padding: 0rem 1.2rem; display: flex; flex-direction: column;">
        <p style="display: flex;align-items: center;font-size: 1rem;color: white; margin-bottom: 15px;" @click="openModal()">
          スイムラブスコア
          <span style="margin-left: 1rem;font-size: 1rem;" class="material-icons">error_outline</span>
        </p>
        <div style="display: flex; margin-bottom: 3rem;">
          <div style="position: relative; margin-right: 11px">
            <div style="position: relative;">
              <img style="margin-right: 1.5rem;" src="../../../assets/icons/A.png" alt="A">
              <div style="position: absolute; right: 5px; bottom: 0; color: white;">78</div>
            </div>
            <img style="position: absolute; right: 5px; top: 0;" src="../../../assets/icons/Arrow-01.png" alt="A">
          </div>
          <v-ons-card style="margin: 0; padding: 0.3rem 0.6rem;display: flex;justify-content: space-between;box-shadow: 0 0px 0px rgb(0 0 0 / 12%);">
            <span style="font-size: 0.85rem;">とても頑張っていますね！コーチからの評価も非常に高いです！</span>
          </v-ons-card>
        </div>
      </div>
      <div>
        <p style="padding-left: 2rem;">スイムラブスコア推移</p>
        <div class="chart">
            <img style="position: absolute;" src="../../../assets/images/Line.png" alt="">
            <img style="position: absolute;top: 33%;" src="../../../assets/images/Line.png" alt="">
            <img style="position: absolute;top: 66%;" src="../../../assets/images/Line.png" alt="">
            <img style="position: absolute;top: 100%;" src="../../../assets/images/Line.png" alt="">
            <template v-for="(mark, key) in marks">
                <single-chart
                  :key="key"
                  :marks="mark"
                  :max_marks="100"
                  :color1="color1[key]"
                  :color2="color2[key]"
                  :data="data[key]">
                </single-chart>
            </template>
        </div>
        <p style="text-align: right;padding-right: 2rem;padding-top: 1rem; color: #F85D95;">A78</p>
      </div>
      <div style="margin: 10px 1.5rem; position: relative;margin-bottom: 10rem;">
        <p style="margin-top: 0px;">友達リスト : 100</p>
        <div style="position: absolute; top: 0; right: 0; color: #0089FF;">
          + 友達を追加
        </div>
      </div>
      <div class="tab-bottom">
        <div style="text-align: center">
          <img src="../../../assets/icons/List.png" alt="">
          <p style="margin: 0">サマリー</p>
        </div>
        <div style="text-align: center">
          <img style="width: 18px; height: 18px; margin: 3px" src="../../../assets/icons/Book.png" alt="">
          <p style="margin: 0">スイムノート</p>
        </div>
      </div>
    </div>

    <div class="x01 screen qr-back">
        <v-ons-dialog
            style="width: 100%; text-align: center;"
            modifier="select-modal1"
            cancelable
            :visible.sync="dialogVisible"
        >
            <v-ons-page style="text-align: center;">
                <v-ons-card style="background-color: white; margin: 0; text-align: center">
                  <p>選手の切り替え</p>
                  <v-ons-list style="background:none">
                      <v-ons-list-item v-for="(item, index) in items" :key="index" @click="changeSelectItem(index)"
                          class="player-list-item" style="border-bottom: solid 1px white"
                      >
                          <div style="margin-left: 0rem; width: calc(98% - 2rem)">{{item.key}}</div>
                          <v-ons-checkbox
                            :input-id="'checkbox-' + index"
                            :value="false"
                            v-model="items[index].value"
                          >
                          </v-ons-checkbox>
                      </v-ons-list-item>
                  </v-ons-list>
                </v-ons-card>
            </v-ons-page>
        </v-ons-dialog>
    </div>
  </div>
</template>

<script>
  import LSideBar from '../../layout/LSideBar';
  import FocusText from '../../layout/components/FocusText';
  import SingleChart from '../practice/components/SingleChart';
  import Friend from '../top/components/Friend';
  export default {
    name: "member-chart",
    components: {
      FocusText,
      SingleChart,
      Friend,
      LSideBar,
    },
    computed: {
      bodyStyle() {
        if (this.opened) {
          return {"height": "100vh","overflow": "hidden"}
        } else {
          return {"height": "auto"}
        }
      }
    },
    data() {
      return {
        color1: ["#F85D95", "#F8CC5D", "#5DF8AD", "#F85D95", "#F89E5D", "#F89E5D", "#F85D95", "#F89E5D", "#F85D95", "#F85D95",],
        color2: ["#E22B6D", "#E2AF2B", "#16CF76", "#E22B6D", "#E2572B", "#E2572B", "#E22B6D", "#E2572B", "#E22B6D", "#E22B6D"],
        marks: ["100", "60", "30", "90", "60", "60", "90", "80", "90", "100"],
        data: ["2/3", "2/4", "2/10", "2/17", "2/18", "3/4", "3/9", "3/12", "3/13", "3/17"],
        friendImgs: [
          "/static/assets/images/img-01.png",
          "/static/assets/images/img-02.png",
          "/static/assets/images/img-03.png",
          "/static/assets/images/img-04.png",
          "/static/assets/images/img-05.png",
        ],
        names: [
          "山ちゃん",
          "田中",
          "たけ",
          "せや",
          "やま",
        ],
        data1: [
          'B63',
          'A88',
          'A88',
          'A88',
          'A88',
        ],
        dataColor: [
          '#F89E5D',
          '#F85D95',
          '#F85D95',
          '#F85D95',
          '#F85D95',
        ],
        opened: false,
        opened_player_info: false,
        opened_modal: true,

        dialogVisible: false,
        items: [ {key: "ひまり", value: true}, {key: "ひまりの兄弟", value: false}],
      }
    },
    methods: {
      toggleLeftSideBar() {
        this.opened = !this.opened;
      },
      togglePlayerData() {
        this.opened_player_info = !this.opened_player_info;
      },
      openModal() {
        console.log("ASDF")
        this.opened_modal = true;
      },
      closeModal() {
        this.opened_modal = false;
      },
      changeSelectItem(index) {
        //this.items = this.items.map((item, id) => id == index ? ({...item, value: true}) : ({...item, value: false}));
      }
    }
  }
</script>

<style scoped>
  div.row {
    display: flex;
  }
  div.chart {
      display: flex;
      justify-content: space-between;
      padding: 0rem 2.2rem;
      position: relative;
  }
  .tab-bottom {
    position: fixed; bottom: 0;width: 100%;display: flex;flex-direction: row;flex-wrap: nowrap;justify-content: space-around;
    padding-top: 1.5rem;
    padding-bottom: 2rem;
    background: white;
    border-top: 1px solid lightgray;
    border-top-left-radius: 0.5rem;
    border-top-right-radius: 0.5rem;
  }
</style>
