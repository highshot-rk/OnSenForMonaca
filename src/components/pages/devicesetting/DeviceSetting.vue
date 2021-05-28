<template>
  <v-ons-page>
    <div>
      <div class="mx-auto">
        <v-ons-toolbar class="practice-toolbar" style="margin-top: 0rem">
          <div class="left">
            <v-ons-back-button style="color: #5496D7">
              <v-ons-icon size="1rem" icon="md-close, material:md-close"></v-ons-icon>
            </v-ons-back-button>
          </div>
          <div class="center" style="text-align: center;" :style="!isSaved?'margin-left: -1.5rem':''">
            <span class="toolbar-title textlabel-my text-bold-black-18px">{{!isSaved?'チームに参加する選手を用意':'選手を編集'}}</span>
          </div>
          <div class="right" style="color: #5496D7;">
            <v-ons-button @click="deleteDialogVisible = true" v-if="isSaved" style="background:none;color: #5496D7;">
              <v-ons-icon style="padding-right: .5rem" size="1rem" icon="fa-trash"></v-ons-icon>
            </v-ons-button>
          </div>
        </v-ons-toolbar>
      </div>
      <!-- <div class="header">
        <v-ons-back-button modifier="quiet">
          <v-ons-icon size="1rem" icon="arrow-left, material:arrow-left"></v-ons-icon>
        </v-ons-back-button>
        <span class="h_title">プロフィールを設定して始める</span>
      </div> -->
      <v-ons-card class="card-item" style="margin-top: 3.9rem; padding-top: 0.2rem; background-color: #EFEFEF;">
        <div class="paragraph" style="margin-top: 2rem">
          <img src="/static/images/on.png" alt="Smiley face" style="float:right;width:60px;height:60px;">
          <p style="vertical-align: middle;padding-right: 5rem">1. スピーカー機器の電源を入れてください。</p>
        </div>
        <div class="paragraph">
          <img src="/static/images/on_b.png" alt="Smiley face" style="float:right;width:60px;height:60px;">
          <p style="vertical-align: middle;padding-right: 5rem">2. スピーカー機器をBluetoothのペアリングモードにしてください。</p>
        </div>
        <div class="paragraph">
          <p style="vertical-align: middle">3. モバイル機器の「設定」からBluetooth設定を開き、「その他の機器」からスピーカー機器を選択してください。</p>
          <p class="mx-auto" style="width: fit-content">
            <img src="/static/images/b1.png" alt="Smiley face" style="margin:auto;width:200px;height:100px">
          </p>
        </div>
        <div class="paragraph">
          <p style="vertical-align: middle">4. ペアリングされた機器が「自分のデバイス」の下に表示されていることを確認できれば完了です。</p>
          <p class="mx-auto" style="width: fit-content">
            <img src="/static/images/b1.png" alt="Smiley face" style="margin:auto;width:200px;height:100px">
          </p>
        </div>
        <div class="button-div" style="margin-top: 1rem;">
          <v-ons-button class="bold-white-16px-white mx-auto button-long-primary-normal-my mt-2" style="border-radius: 30px;width: 84.5vw;padding: 14px 96px;">システム環境設定を開く</v-ons-button>
        </div>
      </v-ons-card>
    </div>
  </v-ons-page>
</template>

<script>

export default {
    name: "memberprofilephoto",
    data() {
      return {
        photo_url: 'static/images/no_user.png',
        actionSheetVisible: false,
        full_name: '',
        isSaved: false,
        isLinked: false,
        deleteDialogVisible: false,
      }
    },
    methods: {
      close_modal(){
        this.actionSheetVisible = false;
      },
      save() {
        this.isSaved = true;
      },
      link() {
        this.isLinked = true;
      },
      deleteMember() {
        this.isSaved = false;
        this.isLinked = false;
        this.deleteDialogVisible = false;
        this.$ons.notification.toast('選手を削除しました', {timeout: 2000, modifier: 'my-toast-higher'});
      }
    }

}
</script>

<style scoped>
  .paragraph{
    padding: .5rem;
  }
  .paragraph p{
    font-family: SF Pro Text;
    font-style: normal;
    font-weight: normal;
    font-size: 14px;
    line-height: 150%;
    color: #303235;
    padding: .3rem;
    margin-top: .3rem;
  }
  .card-item {
    margin: 0.2rem 0 0 0;
    width: 100%;
    padding: 0.5rem;
    border-radius: 0.1rem;
    height: calc(100vh - 3.9rem);
    overflow: auto;
  }
  .bold-white-16px-white{
    font-family: Noto Sans CJK JP-medium;
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    /* line-height: 150%; */
    text-align: center;
    color: #FFFFFF;
  }
</style>
