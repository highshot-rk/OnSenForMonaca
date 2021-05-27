<template>
  <!-- <v-ones-page class="slide-page"> -->
    <div class="sidebar-back" :style="{display: open ? 'inherit' : 'none'}">
        <div class="l-side-bar-back" @click="hide()"></div>
        <div class="l-side-bar">
            <div class="logo">
                <img src="../../assets/images/logo-girl.png" alt="" />
                <div class="info">
                    <p>コーチ田中</p>
                    <p>ID:XXXXXXXXXXXXXXX</p>
                </div>
            </div>
            <div class="menu">
                <div class="menu-item">
                    <v-ons-icon class="menu-item-icon" icon="fa-user"></v-ons-icon>
                    <p>プロフィール編集</p>
                </div>
                <div class="menu-item">
                    <v-ons-icon class="menu-item-icon" icon="fa-user-friends"></v-ons-icon>
                    <p>チーム設定</p>
                </div>
                <div class="menu-item">
                    <v-ons-icon class="menu-item-icon" icon="fa-cog"></v-ons-icon>
                    <p>機器連携設定</p>
                </div>
            </div>
            <div class="bottom-menu" style="padding-bottom: 3rem;">
                <div class="menu-item" @click="logout()">
                    <img src="../../assets/icons/Logout.png" />
                    <p>アカウント情報編集</p>
                </div>
                <div class="menu-item">
                    <img src="../../assets/icons/List.png" />
                    <p>利用規約</p>
                </div>
                <div class="menu-item">
                    <img src="../../assets/icons/Text.png" />
                    <p>ログアウト</p>
                </div>
            </div>
        </div>

        <div>
          <v-ons-action-sheet
            :visible.sync="actionSheetVisible"
            cancelable
            title="<span style='font-family: Noto Sans JP;
                    font-style: normal;
                    font-weight: bold;
                    font-size: 16px;
                    line-height: 150%;
                    text-align: center;
                    color: #303235;'>ログアウトしますか？</span>"
          >
            <v-ons-action-sheet-button icon="md-square-o" @click="close_modal()"><span>ログアウト</span></v-ons-action-sheet-button>
            <v-ons-action-sheet-button icon="md-square-o" @click="close_modal()"><span>キャンセル</span></v-ons-action-sheet-button>
          </v-ons-action-sheet>
        </div>
    </div>
  <!-- </v-ones-page> -->
</template>

<script>
import FocusText from './components/FocusText';

export default {
    name: 'l-side-bar',
    components: {
      FocusText,
    },
    data() {
      return {
        actionSheetVisible: false,
      }
    },
    props: [
      "open"
    ],
    methods: {
      hide() {
        if (this.open) {
          this.$emit("hide-sidebar");
        }
      },
      logout() {
        this.open_modal();
        this.hide();
      },
      open_modal() {
        this.actionSheetVisible = true;
      },
      close_modal(){
        this.actionSheetVisible = false;
      }
    }
}
</script>

<style scoped>
    .sidebar-back {
        /* display: none; */
        height: 100vh;
    }
    .sidebar-back .l-side-bar-back {
        display: flex;
        background: black;
        height: 100%;
        opacity: 0.3;
        position: absolute;
        left: 0;
        width: 100%;
        z-index: 9999;
    }
    .l-side-bar {
        position: absolute;
        left: 0;
        top: 0;
        width: calc(100vw - 5rem);
        z-index: 9999;
        height: 100%;
        background: #ffffff;
        padding-left: 1rem;
        /* display: none; */
        display: flex;
        flex-direction: column;
    }
    .logo {
        position: relative;
        flex: 0 0 auto;
    }
    .logo img {
        position: absolute;
        left: 0.7rem;
        top: 1.2rem;
        width: 4rem;
        height: 4rem;
    }
    .logo .info {
        margin-left: 5rem;
        margin-top: 1.5rem;
        top: 0;
    }
    .logo .info p:first-child {
        font-weight: bold;
        text-align: left;
        margin-bottom: 5px;
    }
    .logo .info p:last-child {
        font-size: 0.7rem;
        text-align: left;
        margin-bottom: 5px;
    }
    .menu {
        flex: 0 0 auto;
        padding-top: 2.5rem;
    }
    .menu-item {
        position: relative;
    }
    .menu-item-icon {
        position: absolute;
        left: 0;
        top: 0;
        font-size: 1.2rem;
        color: #5496D7;
    }
    .menu-item img {
        position: absolute;
        left: 0;
        top: 0;
        font-size: 2rem;
        color: #5496D7;
    }
    .menu-item p {
        margin-left: 3rem;
        margin-bottom: 0rem;
        margin-top: 2rem;
        text-align: left;
        color: #000;
    }
    div.bottom-menu {
        margin-top: auto;
        flex: 1 1 auto;
        display: flex;
        flex-direction: column-reverse;
    }
    .bottom-menu .menu-item {
      position: relative;
    }
    .bottom-menu .menu-item p, .bottom-menu .menu-item img {
      margin-top: 2rem;
    }
</style>
