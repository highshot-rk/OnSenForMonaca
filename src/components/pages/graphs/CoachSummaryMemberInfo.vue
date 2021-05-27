<template>
  <v-ones-page class="slide-page">
    <l-side-bar
      :open="opened"
      @hide-sidebar="toggleLeftSideBar()"
    ></l-side-bar>
    <div :style="bodyStyle">
      <div style="background: lightgray;height: 2.5rem"></div>
      <div class="row" style="margin-top: -5px; background: white;padding-top: 1rem;border-top-left-radius: 0.5rem;border-top-right-radius: 0.5rem;">
        <span class="material-icons" style="width: 1rem; height:1rem; margin-top: 1rem; margin-left: 1rem;color: #5496D7;" alt=""  @click="toggleLeftSideBar()">arrow_back</span>
        <img style="width: 5rem; height: 5rem" src="../../../assets/images/student-girl.png" alt=""/>
        <div class="info">
            <p style="margin-top: 5px;"><b>ひまり</b></p>
            <p style="display: flex;"><focus-text>バタフライ 100m</focus-text></p>
            <template v-if="!opened_player_info">
            <p @click="togglePlayerData()" style="position: relative; font-size: 0.7rem; color: #303235;"><span style="margin-left: 0rem">ベストタイム : 04:34 | 目標 : 03:50</span></p>
            </template>
        </div>
      </div>
      <div class="row" style="background: url('/static/assets/images/blue-water-bg.png'); padding: 0rem 1.2rem; display: flex; flex-direction: column;">
        <p style="display: flex;font-size: 1rem;color: white; margin-bottom: 15px;display: flex; align-items: center;" @click="openModal()">SwimLab<span style="margin-left: 1rem;font-size: 0.6rem;" class="material-icons">error_outline</span></p>
        <div style="display: flex; margin-bottom: 3rem;">
          <div style="position: relative; margin-right: 11px">
            <div style="position: relative;">
              <img style="margin-right: 2rem;height: 35px;" src="static/assets/icons/B.png" alt="B">
              <div style="position: absolute; right: 5px; bottom: 0; color: white;">63</div>
            </div>
            <span class="material-icons" style="position: absolute; right: 5px; top: 0;color: white;">south_east</span>
          </div>
          <v-ons-card style="margin: 0; padding: 0.3rem 0.6rem;display: flex;justify-content: space-between;box-shadow: 0 0px 0px rgb(0 0 0 / 12%);flex: 1 1 auto;">
            <span style="font-size: 0.85rem;color: #303235;">少し下がってきています。</span>
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
      <div class="tab-bottom">
        <div style="text-align: center">
          <img src="../../../assets/icons/List.png" alt="">
          <p style="margin: 0">サマリー</p>
        </div>
        <div style="text-align: center">
          <img style="width: 18px; height: 18px; margin: 3px" src="../../../assets/icons/Book.png" alt="">
          <p style="margin: 0">練習メニュー</p>
        </div>
        <div style="text-align: center">
          <img style="width: 18px; height: 18px; margin: 3px" src="../../../assets/icons/Book.png" alt="">
          <p style="margin: 0">スイムノート</p>
        </div>
      </div>
    </div>
    <modal :open="opened_modal" @close-modal="closeModal()">
      <h2 style="text-align: center; color: #0060D0">スイムラブスコア とは</h2>
      <div style="width: 100%; text-align: center;">
        <img style="margin: auto;" src="../../../assets/images/bar-chart-demo.png" alt="" />
      </div>
      <pre>
        ｢スイムラブスコア｣は、
        練習への取り組みや
        目標に対する進捗率から算出される
        独自のスコアです。

        スイムラブスコアを目安に、
        楽しく目標達成を目指しましょう！
      </pre>
      <div style="width: 100%;">
        <v-ons-button
            modifier="large"
            style="max-width: 15rem;margin: auto;border-radius: 100px;"
            @click="closeModal()"
        >次へ</v-ons-button>
      </div>
    </modal>
  </v-ones-page>
</template>

<script>
  import LSideBar from '../../layout/LSideBar';
  import FocusText from '../../layout/components/FocusText';
  import SingleChart from '../practice/components/SingleChart';
  import Friend from '../top/components/Friend';
  import Modal from '../top/components/Modal';
  export default {
    name: "member-chart",
    components: {
      FocusText,
      SingleChart,
      Friend,
      LSideBar,
      Modal,
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
        opened_modal: false,
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
