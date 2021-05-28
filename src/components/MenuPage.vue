<template>
  <v-ons-page>
    <v-ons-button @click="push('WelcomeOfferCoach')">1 welcomeoffercoach</v-ons-button>
    <v-ons-button @click="push('ProCoachOfferCoach')">1 ProCoachOfferCoach</v-ons-button>
    <v-ons-button @click="push('ProSwimmerOfferPlayer')">1 ProSwimmerOfferPlayer</v-ons-button>
    <v-ons-button @click="push('SupporterProSwimmerOffer')">1 SupporterProSwimmerOffer</v-ons-button>
    <v-ons-button @click="push('PracticeList')">1 PracticeList</v-ons-button>
    <v-ons-button @click="push('Practice2')">1 Practice2</v-ons-button>
    <v-ons-button @click="push('Practice3')">1 Practice3</v-ons-button>
    <v-ons-button @click="push('PracticeNew')">1 PracticeNew</v-ons-button>
    <v-ons-button @click="push('HomePage')">2 HomePage</v-ons-button>
    <v-ons-button @click="push('Boarding')">2 Boarding</v-ons-button>
    <v-ons-button @click="push('Profile')">4 Profile</v-ons-button>
    <v-ons-button @click="push('Race')">4 Race</v-ons-button>
    <v-ons-button @click="push('Manage')">2 Ex/Manage</v-ons-button>
    <v-ons-button @click="push('Relax')">2 Ex/Relax</v-ons-button>
    <v-ons-button @click="push('Train')">2 Ex/Train</v-ons-button>
    <v-ons-button @click="push('LSideBar')">2 Layout/LSideBar</v-ons-button>
    <v-ons-button @click="push('MemberSummery')">2 Top/MemberSummery</v-ons-button>
    <v-ons-button @click="push('MemberSummeryStep1')">2 Top/MemberSummeryStep1</v-ons-button>
    <v-ons-button @click="push('MemberSummeryStep2')">2 Top/MemberSummeryStep2</v-ons-button>
    <v-ons-button @click="push('Menu1')">2 PracticImplement/Menu1</v-ons-button>
    <v-ons-button @click="push('Menu1_1')">2 PracticImplement/Menu1-1</v-ons-button>
    <v-ons-button @click="push('PracticeList')">1 PracticeList</v-ons-button>
    <v-ons-button @click="push('PracticeSearch')">4 PracticeSearch</v-ons-button>
    <v-ons-button @click="push('WelcomeOfferCoach')">1 welcomeoffercoach</v-ons-button>
    <v-ons-button @click="push('ProCoachOfferCoach')">1 ProCoachOfferCoach</v-ons-button>
    <v-ons-button @click="push('ProSwimmerOfferPlayer')">1 ProSwimmerOfferPlayer</v-ons-button>
    <v-ons-button @click="push('SupporterProSwimmerOffer')">1 SupporterProSwimmerOffer</v-ons-button>
    <v-ons-button @click="push('PracticeList')">1 PracticeList</v-ons-button>
    <v-ons-button @click="push('Practice2')">1 Practice2</v-ons-button>
    <v-ons-button @click="push('Practice3')">1 Practice3</v-ons-button>
    <v-ons-button @click="push('PracticeEdit')">1 PracticeEdit</v-ons-button>
    <v-ons-button @click="push('SetItem')">1 SetItem</v-ons-button>
    <v-ons-button @click="push('MenuTypeList')">1 MenuTypeList</v-ons-button>
    <v-ons-button @click="push('MenuLevelList')">1 MenuLevelList</v-ons-button>

    <v-ons-button @click="push('MenuContentList')">1 MenuContentList</v-ons-button>
    <v-ons-button @click="push('MenuItemList')">1 MenuItemList</v-ons-button>
    <v-ons-button @click="push('SetupAccount')">1 SetupAccount</v-ons-button>
    <v-ons-button @click="push('ParticipatingTeam')">1 ParticipatingTeam</v-ons-button>
    <v-ons-button @click="push('ParentsProfile')">1 ParentsProfile</v-ons-button>
    <v-ons-button @click="push('ParentConnect01')">1 ParentConnect01</v-ons-button>
    <v-ons-button @click="push('ChildrenList')">1 ChildrenList</v-ons-button>

    <v-ons-button @click="push('HomePage')">2 HomePage</v-ons-button>
    <v-ons-button @click="push('Boarding')">2 Boarding</v-ons-button>
    <v-ons-button @click="push('Profile')">4 Profile</v-ons-button>
    <v-ons-button @click="push('Race')">4 Race</v-ons-button>
    <v-ons-button @click="push('Manage')">2 Ex/Manage</v-ons-button>
    <v-ons-button @click="push('Relax')">2 Ex/Relax</v-ons-button>
    <v-ons-button @click="push('Train')">2 Ex/Train</v-ons-button>
    <v-ons-button @click="push('MemberSummery')">2 Top/MemberSummery</v-ons-button>
    <v-ons-button @click="push('MemberSummeryStep1')">2 Top/MemberSummeryStep1</v-ons-button>
    <v-ons-button @click="push('MemberSummeryStep2')">2 Top/MemberSummeryStep2</v-ons-button>
    <v-ons-button @click="push('SelfEvaluation')">2 Top/SelfEvaluation</v-ons-button>
    <v-ons-button @click="push('Menu1')">2 PracticImplement/Menu1</v-ons-button>
    <v-ons-button @click="push('Menu1_1')">2 PracticImplement/Menu1-1</v-ons-button>
    <v-ons-button @click="push('Evaluation')">2 PracticImplement/Evaluation</v-ons-button>
    <v-ons-button @click="push('Practicalend')">2 Pracitc/PracticalEnd</v-ons-button>
    <v-ons-button @click="push('Practicalresult')">2 Pracitc/PracticalResult</v-ons-button>

    <v-ons-button @click="push('PracticeList1')">2 PracticalMenu/PracticeList</v-ons-button>
    <v-ons-button @click="push('PracticeDone')">2 PracticalMenu/PracticeDone</v-ons-button>
    <v-ons-button @click="push('PracticeReady')">2 PracticalMenu/PracticeReady</v-ons-button>
    <v-ons-button @click="push('TeamEvalStatus')">2 PracticalMenu/TeamEvalStatus</v-ons-button>
    <v-ons-button @click="push('SwimNote')">2 SwimNote/SwimNote</v-ons-button>
    <v-ons-button @click="push('SingleSwimNote')">2 SwimNote/SingleSwimNote</v-ons-button>
    <v-ons-button @click="push('SwimNoteOne')">2 SwimNote/SwimNoteOne</v-ons-button>
    <v-ons-button @click="push('ParentMemberSummary')">2 Graphes/MemberSummary</v-ons-button>
    <v-ons-button @click="push('ParentSwimNote')">2 Graphes/ParentSwimNote</v-ons-button>
    <v-ons-button @click="push('CoachSummary')">2 Graphes/CoachSummary</v-ons-button>
    <v-ons-button @click="push('CoachSummaryMemberInfo')">2 Graphes/CoachSummaryMemberInfo</v-ons-button>

    <v-ons-button @click="push('Signup')">3 sign/SIGNUP</v-ons-button>
    <v-ons-button @click="push('Login')">3 sign/LOGIN</v-ons-button>
    <v-ons-button @click="push('Agree')">3 sign/AGREE</v-ons-button>
    <v-ons-button @click="push('Mailsent')">3 sign/MAILSENT</v-ons-button>
    <v-ons-button @click="push('Lensetting1', {type: 1})">3 lensetting/Lensetting1</v-ons-button>
    <v-ons-button @click="push('Lensetting1', {type: 2})">3 lensetting/Lensetting2</v-ons-button>
    <v-ons-button @click="push('Lensetting1', {type: 3})">3 lensetting/Lensetting3</v-ons-button>
    <v-ons-button @click="push('SettingAddress')">3 lensetting/SettingAddress</v-ons-button>
    <v-ons-button @click="push('SettingClock')">3 lensetting/SettingClock</v-ons-button>
    <v-ons-button @click="push('CountDown10')">3 lensetting/CountDown10</v-ons-button>
    <v-ons-button @click="push('SettingVolume')">3 lensetting/SettingVolume</v-ons-button>

    <v-ons-button @click="push('DeviceSetting')">3 devicesetting/DeviceSetting</v-ons-button>
    <v-ons-button @click="push('TeamSetting')">3 team/TeamSetting</v-ons-button>
    <v-ons-button @click="push('QR_Code')">3 team/QR_Code(member)</v-ons-button>
    <v-ons-button @click="push('CoachSummaryT')">3 team/CoachSummaryT</v-ons-button>
    <v-ons-button @click="push('AddChild')">3 team/AddChild</v-ons-button>
    <v-ons-button @click="push('AddChildSuccess')">3 team/AddChildSuccess</v-ons-button>

    <v-ons-button @click="push('FamilySetting')">4 FamilySetting</v-ons-button>
    <v-ons-button @click="push('Policy')">4 Policy</v-ons-button>

  </v-ons-page>
</template>

<script>
import WelcomeOfferCoach from "./pages/subscription/WelcomeOfferCoach";
import ProCoachOfferCoach from "./pages/subscription/ProCoachOfferCoach";
import ProSwimmerOfferPlayer from "./pages/subscription/ProSwimmerOfferPlayer";
import SupporterProSwimmerOffer from "./pages/subscription/SupporterProSwimmerOffer";

import PracticeList from "./pages/practicemenulist/PracticeList";
import Practice2 from "./pages/practicemenulist/Practice2";
import Practice3 from "./pages/practicemenulist/Practice3";

import PracticeNew from "./pages/practicemanage/PracticeNew";
import PracticeEdit from "./pages/practicemanage/PracticeEdit";
import SetItem from "./pages/practicemanage/SetItem";
import MenuTypeList from "./pages/practicemanage/MenuTypeList";
import MenuLevelList from "./pages/practicemanage/MenuLevelList";
import MenuContentList from "./pages/practicemanage/MenuContentList";
import MenuItemList from "./pages/practicemanage/MenuItemList";
import SetupAccount from "./pages/setup/SetupAccount";
import ParticipatingTeam from "./pages/teamlist/ParticipatingTeam";
import ParentsProfile from "./pages/parents/ParentsProfile";
import ParentConnect01 from "./pages/parents/ParentConnect01";
import ChildrenList from "./pages/parents/childs/ChildrenList";

import HomePage from "./pages/boarding/HomePage";
import Boarding from "./pages/boarding/Boarding";
import Profile from "./pages/profile/Profile";
import Race from "./pages/Race/Race";
import Manage from "./pages/practice/Manage";
import Relax from "./pages/practice/Relax";
import Train from "./pages/practice/Train";

import LSideBar from "./layout/LSideBar";
import MemberSummery from "./pages/top/MemberSummery";
import MemberSummeryStep1 from "./pages/top/MemberSummeryStep1";
import MemberSummeryStep2 from "./pages/top/MemberSummeryStep2";
import SelfEvaluation from "./pages/top/SelfEvaluation";

import Menu1 from "./pages/practiceimplement/Menu1";
import Menu1_1 from "./pages/practiceimplement/Menu1_1";
import Evaluation from "./pages/practiceimplement/Evaluation";
import Practicalresult from "./pages/practicalresult/Practicalresult";
import Practicalend from "./pages/practicalresult/Practicalend";

import PracticeList1 from './pages/practicalmenu/PracticeList';
import PracticeDone from './pages/practicalmenu/PracticeDone';
import PracticeReady from './pages/practicalmenu/PracticeReady';
import TeamEvalStatus from './pages/practicalmenu/TeamEvalStatus';
import SwimNote from './pages/swimnote/SwimNote';
import SingleSwimNote from './pages/swimnote/SingleSwimNote';
import SwimNoteOne from './pages/swimnote/SwimNoteOne';

import ParentMemberSummary from './pages/graphs/MemberSummary';
import ParentSwimNote from './pages/graphs/SwimNote';
import CoachSummary from './pages/graphs/CoachSummary';
import CoachSummaryMemberInfo from './pages/graphs/CoachSummaryMemberInfo';

import Signup from "./pages/sign/Signup";
import Login from "./pages/sign/Login";
import Agree from "./pages/sign/Agree";
import Mailsent from "./pages/sign/Mailsent";

import Lensetting1 from "./pages/Lensetting/Setting1";
import SettingAddress from "./pages/Lensetting/SettingAddress";
import SettingClock from "./pages/Lensetting/SettingClock";
import CountDown10 from "./pages/Lensetting/CountDown10";
import SettingVolume from "./pages/Lensetting/SettingVolume";
import TeamSetting from "./pages/team/TeamSetting";
import QR_Code from "./pages/team/QR_Code";
import AddChild from "./pages/team/AddChild";
import AddChildSuccess from "./pages/team/AddChildSuccess";

import CoachSummaryT from "./pages/top/CoachSummaryT";
import DeviceSetting from "./pages/devicesetting/DeviceSetting";

import PracticeSearch from './pages/practicesearch/PracticeSearch';
import FamilySetting from './pages/familysetting/FamilySetting';
import Policy from "./pages/policy/Policy";

export default {
  name: 'menulist',
  data(){
    return {
      components: {
        WelcomeOfferCoach,
        ProCoachOfferCoach,
        SupporterProSwimmerOffer,
        ProSwimmerOfferPlayer,
        PracticeList,
        Practice2,
        Practice3,
        PracticeNew,
        PracticeEdit,
        SetItem,
        MenuTypeList,
        MenuLevelList,
        MenuContentList,
        MenuItemList,
        SetupAccount,
        ParticipatingTeam,
        ParentsProfile,
        ParentConnect01,
        ChildrenList,
        HomePage,
        Boarding,
        Profile,
        Race,
        Manage,
        Relax,
        Train,
        LSideBar,
        MemberSummery,
        Signup,
        Login,
        Agree,
        Mailsent,
        MemberSummeryStep1,
        MemberSummeryStep2,
        SelfEvaluation,
        Lensetting1,
        SettingAddress,
        SettingClock,
        CountDown10,
        SettingVolume,
        TeamSetting,
        QR_Code,
        Menu1,
        Menu1_1,
        PracticeSearch,
        Evaluation,
        Practicalresult,
        Practicalend,

        FamilySetting,
        Policy,

        PracticeList1,
        PracticeDone,
        PracticeReady,
        TeamEvalStatus,
        SwimNote,
        SingleSwimNote,
        SwimNoteOne,
        CoachSummaryT,
        CoachSummary,
        DeviceSetting,
        AddChild,
        AddChildSuccess,
        ParentMemberSummary,
        ParentSwimNote,
        CoachSummaryMemberInfo,
      },
    }
  },
  methods: {
    push(name, data) {
      if(data)
        this.$emit('push-page', {
          extends: this.components[name],
          data () {
            return {// Set the value you want to pass
              data
        }}});
      else
        this.$emit('push-page', this.components[name]);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.header {
  text-align: center;
  margin-bottom: 20px;
}

img {
  max-width: 150px;
}

ons-list-title {
  text-transform: none;
}

ons-list-item {
  cursor: pointer;
}
</style>
