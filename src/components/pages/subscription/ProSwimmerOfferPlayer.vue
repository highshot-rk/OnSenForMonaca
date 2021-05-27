// Proスイマーオファー_選手

<template>
    <div class="subscription-1">
        <div class="header">
        </div>
        <div class="title">
            <span class="text-font-32" style="font-weight: bolder; letter-spacing: 0.2em;">Proスイマー登録</span>
        </div>
        <img src="../../../assets/images/subscription_proswimmer.png" alt="Subscription_Users" width="100%"/>
        <div class="content text-font-14">
            <v-ons-card class="subscription-card">
                <div class="subscription-card-title"><span class="text-font-18" style="font-weight:bold;">9%お得</span></div>
                <div class="subscription-card-content" style="font-weight:bold;">
                    <div class="subscription-row text-font-24" style="width: 100%; padding: 0;">
                        <div class="text-color-black" style="margin: 0 2rem 0 1.5rem; display: inline;">毎年</div>
                        <div class="text-color-blue" style="margin: 0 0 0 4rem; display: inline;">¥1,300</div>
                    </div>
                    <div class="subscription-row text-font-16 text-color-gray" style="width:100%">
                        <div style="margin: 0 2rem 0 1.5rem; display: inline;">¥1,440</div>
                        <div style="margin: 0 0 0 4rem; display: inline;">月額¥110</div>
                    </div>

                </div>
            </v-ons-card>
            <v-ons-card modifier="large" class="subscription-card" style="background-color: white;border-radius: 1rem; margin-top: 1.5rem;">
                <div style="padding: 0.5rem">
                    <p class="subscription-btn-text-2 text-font-24 text-color-blue">その後は毎年¥9,600</p>
                </div>
            </v-ons-card>
            <p class="text-font-16" style="margin: 2rem; font-weight: bold; text-decoration: underline;font-family: 'Noto Sans CJK JP';">今は登録しない</p>
            <p style="margin: 0;">無料トライアル終了時に請求が開始します</p>
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
    .subscription-row {
        margin: 0.5rem 0 0.5rem 0;
    }
    .subscription-card {
        margin: auto;
        padding: 0.3rem;
        width: 85%;
        background-color: #0089FF;
        box-shadow: 0px 8px 11px rgba(0, 0, 0, 0.2);
        border-radius: 0.8rem;
    }
    .subscription-card-title{
        margin: 1rem 1rem;
        text-align: center;
    }
    .subscription-card-content {
        margin: 0;
        padding: 1rem;
        box-shadow: 0px 8px 11px rgba(0, 0, 0, 0.2);
        border-bottom-left-radius: 0.8rem;
        border-bottom-right-radius: 0.8rem;
        background-color: white;
        font-family: 'SF Pro Text';
    }
    .subscription-btn {
        margin: auto;
        width: 80%;
        background-color: white;
        box-shadow: 0px 8px 11px rgba(0, 0, 0, 0.2);
        border-radius: 0.8rem;
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
