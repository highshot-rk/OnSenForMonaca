// ウェルカムオファー_コーチ
<template>
  <v-ons-page>
    <div class="subscription-1">
        <div class="header">
        </div>
        <div class="title">
            <span class="text-font-32" style="font-weight: bolder; letter-spacing: 0.2em;">ウェルカムオファー</span>
            <span class="text-font-14">
                <p style="margin-bottom: 0">このオファーの期限：</p>
                <p style="margin-top: 0">23時間57分51秒</p>
            </span>
        </div>
        <!-- <div class="content"> -->
            <img src="../../../assets/images/subscription_users.png" alt="Subscription_Users" width="100%"/>
        <!-- </div> -->
        <div class="content text-font-14">
            <v-ons-button modifier="large" class="subscription-btn" style="border-radius: 1rem;">
                <div style="padding: 0.5rem">
                    <p class="subscription-btn-text-1 text-font-14 text-color-black">1週間の無料トライアルを開始</p>
                    <p class="subscription-btn-text-2 text-font-24 text-color-blue">その後は毎年¥9,600</p>
                </div>
            </v-ons-button>
            <p style="margin: 2rem;">無料トライアル終了時に請求が開始します</p>
            <a class="text-font-16" style="margin: 0; font-weight: bold; text-decoration: underline;">標準プランを見る</a>
            <p style="margin-top: 1rem;margin-bottom:0;">自動更新</p>
            <p style="margin: 0.1rem;">いつでもキャンセル</p>
            <div style="margin: 2rem 2rem 0 2rem;">
                お支払いは、購入の確認時にiTunesアカウントに請求されます。自動更新は、現在の期間の終了の少なくとも24時間前にオフされない限り、サブスクリプションは自動的に更新されます。アカウントには、現在の期間が終了する24時間前に更新料金が請求され、更新費用が特定されます。サブスクリプションはユーザーが管理でき、購入後にユーザーのアカウント設定に移動して自動更新をオフにすることができます。無料トライアル期間の未使用部分は、サブスクリプションの購入時に失効します。
            </div>
            <div style="margin: 0.5rem;">
                <span class="text-font-16" style="font-weight: bold;">プライバシーポリシー及び利用規約</span>
            </div>
        </div>
        <div class="footer"></div>
    </div>
  </v-ons-page>
</template>

<script>

export default {
    name: "welcomeoffercoach",
}
</script>

<style scoped>
    .subscription-1 {
        text-align: center;
        align-items: center;
        padding: 1rem,0,1rem,0;
        background: linear-gradient(to bottom, rgb(39,159,251) , rgb(98, 252, 183));
        padding-bottom: 2rem;
        font-family: 'SF Pro Text';
        color: white;
        letter-spacing: 0.1em;
    }
    .title {
        padding-top: 10vh;
    }
    .subscription-btn {
        margin: auto;
        width: fit-content;
        background-color: white;
        box-shadow: 0px 8px 11px rgba(0, 0, 0, 0.2);
        border-radius: 13.1419px;
    }
    .subscription-btn-text-1 {
        /* 1週間の無料トライアルを開始 */
        font-family: "Noto Sans CJK JP";
        font-style: normal;
        font-weight: bold;
        font-size: 14px;
        line-height: 150%;
        margin:0.5rem;
        /* identical to box height, or 21px */
        text-align: center;
    }

    .subscription-btn-text-2 {
        /* その後は毎年¥9,600 */
        /* font-family: "SF Pro Text"; */
        font-style: normal;
        font-weight: bold;
        font-size: 24px;
        line-height: 150%;
        /* identical to box height, or 36px */
        text-align: center;
        margin:0.5rem;
        /* Primary / Blue */
        color: #0089FF;
    }

    p.description {
        text-align: left;
        font-size: 1.1rem;
        color: gray-dark;
    }
    .text-color-blue {
    /* color: rgb(0, 136, 255); */
        color: #0089FF;
    }
    .text-color-black {
        /* color: rgb(48, 50, 53) */
        color: #303235;
    }
    .text-color-gray {
        color: #BCBCBC;
    }
    .background-color-white {
        background: #EFEFEF !important;    
    }
</style>
