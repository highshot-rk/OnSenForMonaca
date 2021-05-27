<template>
  <v-ons-page style="background: #F5F5F5">
    <h4 style="text-align: center;font-weight: bold;margin: 2rem;">練習終了</h4>
    <div style="width: calc(100% - 20px); background: white;padding: 10px;">
      <div style="border-bottom: 0.5px solid #D3D3D3;display: flex;">
        <p style="color: #707070; padding: 0rem 2rem;">日付</p>
        <p>2021年3月27日</p>
      </div>
      <div style="border-bottom: 0.5px solid #D3D3D3;display: flex;">
        <p style="color: #707070; padding: 0rem 2rem;">開始</p>
        <p>18:00</p>
      </div>
      <div style="border-bottom: 0.5px solid #D3D3D3;display: flex;">
        <p style="color: #707070; padding: 0rem 2rem;">場所</p>
        <p>ホームプール名</p>
      </div>
      <div style="border-bottom: 0.5px solid #D3D3D3;display: flex;">
        <p style="color: #707070; padding: 0rem 2rem;">総距離</p>
        <p style="margin-right: 3rem;">200m</p>
        <p style="color: #707070; padding: 0rem 2rem;">総時間</p>
        <p>4分</p>
      </div>

      <div style="padding-top: 10px;border-bottom: 0.5px solid #D3D3D3;display: flex;align-items: center;">
        <img style="padding: 0.8rem; height: 100%;width: auto;" src="/static/assets/images/plusimage.png"/>
        <div style="position: relative;">
          <span style="position: absolute;right: 0;border-radius: 100px;border: 1px solid gray;background: white;color: #707070;" class='material-icons'>close</span>
          <img style="padding: 0.8rem" src="/static/assets/images/swim1.png"/>
        </div>
        <div style="position: relative;">
          <span style="position: absolute;right: 0;border-radius: 100px;border: 1px solid gray;background: white;color: #707070;" class='material-icons'>close</span>
          <img style="padding: 0.8rem" src="/static/assets/images/swim2.png"/>
        </div>
      </div>
      <p style="color: #707070;padding-left: 10px;">メニューリスト</p>
      <div style="padding: 10px;position: relative;">
        <div style="border: 1px solid gray; border-radius: 10px;width: 100%;">
          <div style="display: flex; padding: 10px;align-items: center;">
            <p style="flex: 1 1 auto; font-weight: bold;">メニュー #1</p>
            <v-ons-button style="border-radius: 100px;background: transparent; color: blue;border: 1px solid blue;height: 2rem;display: flex; align-items: center;font-size: 0.9rem;">
              <span class="material-icons">edit</span>
              編集
            </v-ons-button>
            <span class="material-icons">edit</span>
          </div>
          <table style="width: 100%;text-align: center">
            <thead>
              <tr>
                <td>種類</td>
                <td>種目</td>
                <td>内容</td>
                <td>強度</td>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>Swim</td>
                <td>Choice</td>
                <td>Drill</td>
                <td>EN1</td>
              </tr>
            </tbody>
          </table>

          <table class="table-stripe" style="width: 100%;text-align: center;margin-top: 20px;">
            <thead style="background-color: #D3D3D388">
              <tr style="font-size: 0.7rem;">
                <td>セット</td>
                <td>距離</td>
                <td>本数</td>
                <td>サイクル</td>
                <td>セット間</td>
              </tr>
            </thead>
            <tbody>
              <tr style="height: 2rem;">
                <td>#1</td>
                <td>400</td>
                <td>1</td>
                <td>7'0.</td>
                <td>0</td>
              </tr>
              <tr style="height: 2rem;">
                <td>#2</td>
                <td>50</td>
                <td>10</td>
                <td>1'0.</td>
                <td>0</td>
              </tr>
            </tbody>
          </table>
          <p style="padding-left: 2rem;color: #707070;">説明</p>
          <p style="padding-left: 2rem;font-weight: bold;color: #707070;">無し</p>
        </div>

        <v-ons-button @click="checkPracticResult()" style="position: absolute; bottom: 40px; left: 50%; transform: translateX(-50%); color:#8293A3;border-radius: 100px;padding: 10px;text-align: center;display: flex; align-items: center;color: white;">
          <span><b>練習結果を確認</b></span>
          <span class='material-icons'>navigate_next</span>
        </v-ons-button>
      </div>
    </div>

    <v-ons-bottom-toolbar class="tool_bottom">
      <div class="tab-bottom">
        <div style="text-align: center">
          <v-ons-button modifier="quiet" style="color:#8293A3;">
          <span style="width: 18px; height: 18px; margin: 3px;" class='material-icons'>event_note</span>
          <p style="margin: -10px; font-weight: bold;font-size: 10px;">サマリー</p>
          </v-ons-button>
        </div>
        <div style="text-align: center">
          <v-ons-button modifier="quiet">
            <span style="width: 18px; height: 18px; margin: 3px;" class='material-icons'>menu_book</span>
            <p style="margin: -10px; font-weight: bold; font-size: 10px;">スイムノート</p>
          </v-ons-button>
        </div>
      </div>
    </v-ons-bottom-toolbar>
  </v-ons-page>
</template>

<script>
import Practicalresult from './Practicalresult';
export default {
  components: {
  },
  methods: {
    checkPracticResult() {
      this.push_screen.push(Practicalresult);
    }
  }
}
</script>

<style>
  .tab-bottom {
    display: flex;
    justify-content: space-around;
    padding-top: 1rem;
    padding-bottom: 2rem;
    background: white;
    border-top: 1px solid lightgray;
    border-top-left-radius: 0.5rem;
    border-top-right-radius: 0.5rem;
  }
  .tool_bottom{
    height: 82px;
    padding: 0px 40px;
  }
  table.table-stripe tbody tr:nth-child(even) {
    background: #EFF3F7;
  }
</style>
