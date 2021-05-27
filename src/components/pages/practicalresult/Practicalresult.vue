<template>
  <v-ons-page>
    <h4 style="text-align: center;font-weight: bold;margin: 2rem;">練習結果</h4>
    <div style="width: calc(100% - 20px); background: white;padding: 10px; min-height: calc(100vh - 4rem);">
      <table style="width: 100%; text-align: center;">
        <thead>
          <tr>
            <td style="color: #29B9E7;">レーン1</td>
            <td style="color: #E99B04;">レーン2</td>
            <td style="color: #E45A8C;">レーン3</td>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td style="color: #29B9E7;">-</td>
            <td style="color: #E99B04;">-</td>
            <td style="color: #E45A8C;">-</td>
          </tr>
        </tbody>
      </table>
      <div style="display: flex;justify-content: center;">
        <div>
          <template v-for="(lane1, key) in lane1s">
            <head-card :key="key" :title="lane1.title" color="#29B9E7">
              <table :key="key">
                <tbody>
                  <tr :key="key" v-for="(lane1_data, key) in lane1.data">
                    <td>{{lane1_data.no}}</td>
                    <td>{{lane1_data.time}}</td>
                    <td style="color: #0089FF;" class="material-icons">{{lane1_data.check ? "check_circle" : "radio_button_unchecked"}}</td>
                  </tr>
                </tbody>
              </table>
            </head-card>
          </template>
        </div>
        <div>
          <template v-for="(lane2, key) in lane2s">
            <head-card :key="key" :title="lane2.title" color="#E99B04">
              <table :key="key">
                <tbody>
                  <tr :key="key" v-for="(lane2_data, key) in lane2.data">
                    <td>{{lane2_data.no}}</td>
                    <td>{{lane2_data.time}}</td>
                    <td style="color: #0089FF;" class="material-icons">{{lane2_data.check ? "check_circle" : "radio_button_unchecked"}}</td>
                  </tr>
                </tbody>
              </table>
            </head-card>
          </template>
        </div>
        <div>
          <template v-for="(lane3, key) in lane3s">
            <head-card :key="key" :title="lane3.title" color="#E45A8C">
              <table :key="key">
                <tbody>
                  <tr :key="key" v-for="(lane3_data, key) in lane3.data">
                    <td>{{lane3_data.no}}</td>
                    <td>{{lane3_data.time}}</td>
                    <td style="color: #0089FF;" class="material-icons">{{lane3_data.check ? "check_circle" : "radio_button_unchecked"}}</td>
                  </tr>
                </tbody>
              </table>
            </head-card>
          </template>
        </div>
      </div>
      <v-ons-button @click="push_screen.pop()" style="position: absolute; bottom: 30px; text-align: center;border-radius: 100px;color: white;width: calc(100% - 40px);margin: 20px;">
        完了
      </v-ons-button>
    </div>
  </v-ons-page>
</template>

<script>
import HeadCard from './components/HeadCard';
export default {
  components: {
    HeadCard,
  },
  data() {
    return {
      lane1s: [
        {
          title: "セット#1",
          data: [
            {no: 1,time: 15.33,check: true},
            {no: 2,time: 14.57,check: false},
            {no: 3,time: 8.15,check: false},
          ]
        },
        {
          title: "セット#2",
          data: [
            {no: 1,time: 15.33,check: true},
            {no: 2,time: 14.57,check: false},
            {no: 3,time: 8.15,check: false},
            {no: 4,time: 8.15,check: false},
            {no: 5,time: 8.15,check: false},
          ]
        },
      ],
      lane2s: [
        {
          title: "セット#1",
          data: [
            {no: 1,time: 15.33,check: true},
            {no: 2,time: 14.57,check: false},
            {no: 3,time: 8.15,check: false},
            {no: 4,time: 14.57,check: false},
            {no: 5,time: 8.15,check: false},
          ]
        },
        {
          title: "セット#2",
          data: [
            {no: 1,time: 15.33,check: true},
            {no: 2,time: 14.57,check: false},
            {no: 3,time: 8.15,check: false},
            {no: 4,time: 8.15,check: false},
          ]
        },
      ],
      lane3s: [
        {
          title: "セット#1",
          data: [
            {no: 1,time: 15.33,check: true},
            {no: 2,time: 14.57,check: false},
            {no: 3,time: 8.15,check: false},
            {no: 4,time: 14.57,check: false},
          ]
        },
        {
          title: "セット#2",
          data: [
            {no: 1,time: 15.33,check: true},
            {no: 2,time: 14.57,check: false},
            {no: 3,time: 8.15,check: false},
          ]
        },
      ],
    }
  }
}
</script>

<style>

</style>
