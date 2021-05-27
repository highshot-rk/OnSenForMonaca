<template>
  <v-ons-page style="background: white !important;">
    <p style="text-align: center;font-weight:bold">練習結果</p>
    <p style="text-align: center;color: #0089FF">2021.03.17</p>
    <p style="text-align: center;margin-top: 2rem;">本日の練習はいかがでしたか？</p>
    <div style="width: calc(100% - 40px); margin: 20px; position: relative;margin-top: 70px;">
      <p style="font-weight: bold">満足度</p>
      <div style="display: flex;justify-content: space-around;align-items: center;padding-bottom: 0.5rem;">
        <template v-for="(mark) in 5">
          <span @click="setEval(mark)" :key="mark" class='material-icons' style="background: #FEC227;padding: 0;border-radius: 100px;font-size: 3.5rem;" :style="{border: mark == eval_mark ? '2px solid #29B9E7' : 'none',opacity: mark == eval_mark ? '1' : '0.4'}">
            {{(mark == 1) ? "sentiment_very_dissatisfied" : (
              (mark == 2) ? "mood_bad" : (
                (mark == 3) ? "sentiment_neutral" : (
                  (mark == 4) ? "sentiment_satisfied" : "sentiment_very_satisfied"
                )
              )
            )}}
          </span>
        </template>
      </div>
      <p>コメント</p>
      <textarea style="background: #F5F5F5; padding: 20px; border-radius: 10px;border: none;box-shadow: none;width: calc(100% - 40px);" type="text" placeholder="2021.03.17の練習へのコメント" multiple rows="7"/>
    </div>
    <v-ons-button @click="complete()" style="position: fixed; bottom: 30px;border-radius: 100px;width: calc(100% - 40px);margin: 20px;text-align: center;">
      完了
    </v-ons-button>
  </v-ons-page>
</template>

<script>
import MemberSummery from './MemberSummery';
export default {
  data () {
    return {
      eval_mark: 5,
    }
  },
  methods: {
    setEval(mark) {
      this.eval_mark = mark;
    },
    complete() {
      this.push_screen.push(MemberSummery);
      this.$ons.notification.toast('スイムラブスコアが更新されました', {timeout: 2000, class: "text-alignL center"})
    }
  }
}
</script>

<style>

</style>
