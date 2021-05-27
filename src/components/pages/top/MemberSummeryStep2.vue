<template>
  <v-ones-page class="slide-page">
    <l-side-bar
      :open="opened"
      @hide-sidebar="toggleLeftSideBar()"
    ></l-side-bar>
    <div :style="bodyStyle">
      <div style="background: lightgray;height: 2.5rem"></div>
      <div class="row" style="margin-top: -5px; background: white;padding-top: 1rem;border-top-left-radius: 0.5rem;border-top-right-radius: 0.5rem;">
        <img style="width: 1rem; height:1rem; margin-top: 1rem; margin-left: 1rem;" src="../../../assets/icons/Menu.png" alt=""  @click="toggleLeftSideBar()"/>
        <img style="width: 5rem; height: 5rem" src="../../../assets/images/logo-girl.png" alt=""/>
        <div class="info">
            <p style="margin-top: 5px;"><b>ひまり</b></p>
            <p style="display: flex;"><focus-text>バタフライ 100m</focus-text><span style="margin-left: 5px;font-size: 0.7rem;margin-top: 0.2rem;">ベスト : 02:00</span></p>
            <p style="display: flex;"><focus-text>自由形 100m</focus-text><span style="margin-left: 5px;font-size: 0.7rem;margin-top: 0.2rem;">ベスト : 02:00</span></p>
        </div>
      </div>
      <div class="row" style="background: url('/static/assets/images/blue-water-bg.png'); padding: 0rem 1.2rem; display: flex; flex-direction: column;">
        <p style="display: flex;font-size: 1rem;color: white; margin-bottom: 15px;">SwimLab Score<img style="margin-top: 0.2rem;margin-left: 0.6rem;width: 1rem;height: 1rem;" src="../../../assets/icons/ExclamationMark.png" alt=""></p>
        <div style="display: flex; margin-bottom: 3rem;">
          <div style="position: relative; margin-right: 11px">
            <div style="position: relative;">
              <img style="margin-right: 1.5rem;" src="../../../assets/icons/Question.png" alt="Q">
              <div style="position: absolute; right: 5px; bottom: 0; color: white;">_ _</div>
            </div>
            <!-- <img style="position: absolute; right: 5px; top: 0;" src="../../../assets/icons/Arrow-01.png" alt="A"> -->
          </div>
          <v-ons-card style="margin: 0; padding: 0.3rem 0.6rem;display: flex;justify-content: space-between;box-shadow: 0 0px 0px rgb(0 0 0 / 12%);">
            <span style="font-size: 0.85rem;">ベストタイムの設定が完了しました。次に、コーチのQRコードを読み取って、チームに加入しましょう！</span>
          </v-ons-card>
        </div>
      </div>
      <div class="row" style="padding: 1rem 3rem;">
        <v-ons-button
            modifier="large"
            style="border-radius: 100px"
        >QRコードを読み取り</v-ons-button>
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
        <!-- <p style="text-align: right;padding-right: 2rem;padding-top: 1rem; color: #F85D95;">A78</p> -->
      </div>
      <div style="margin: 2rem 1.5rem 1rem 1.5rem; position: relative;">
        <p style="margin-bottom: 0px;">友達リスト</p>
      </div>
      <p style="text-align: center; margin: 1rem auto">まだ友達が追加されていません</p>
      <p style="text-align: center;color: #0089FF;margin-bottom: 8rem;">
        <b>+</b> 友達を追加
      </p>
      <!-- <div class="friend-group" style="overflow: scroll;margin-bottom: 10rem;">
        <div style="width: fit-content; display: flex;">
          <template v-for="(imgUrl, key) in friendImgs">
            <friend v-bind:key="key" :imgUrl="imgUrl" :name="names[key]" :data="data[key]" :dataColor="dataColor[key]"></friend>
          </template>
        </div>
      </div> -->
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
  </v-ones-page>
</template>

<script>
  import LSideBar from '../../layout/LSideBar';
  import FocusText from '../../layout/components/FocusText';
  import SingleChart from '../practice/components/SingleChart';
  import Friend from './components/Friend';
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
        marks: ["0", "0", "0", "0", "0", "0", "0", "0", "0", "0"],
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
        dataColor: [
          '#F89E5D',
          '#F85D95',
          '#F85D95',
          '#F85D95',
          '#F85D95',
        ],
        opened: false,
        opened_player_info: false,
      }
    },
    methods: {
      toggleLeftSideBar() {
        this.opened = !this.opened;
      },
      togglePlayerData() {
        this.opened_player_info = !this.opened_player_info;
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
