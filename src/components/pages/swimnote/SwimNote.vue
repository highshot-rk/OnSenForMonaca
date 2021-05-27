<template>
  <v-ons-page>
    <div class="page-title">
      <p style="text-align: center;">スイムノート</p>
    </div>
    <div class="card" :key="index" v-for="(cardData, index) in cardDatas">
      <div class="card-body">
        <img style="width: 100%; height: 193px;" :src="cardData.img" alt="">
        <span style="position: absolute;top: 1rem;color: white;font-weight: bold;left: 1rem;font-size: 2rem;">{{cardData.date}}</span>
        <span style="position: absolute;top: 1.5rem;color: white;font-weight: bold;left: 7rem;font-size: 1.2rem;">{{cardData.day}}</span>
        <span style="position: absolute;top: 3rem;color: white;font-weight: bold;left: 1rem;font-size: 1.2rem;">{{cardData.year}}</span>
        <span style="position: absolute;bottom: 4rem;color: white;font-weight: bold;left: 1rem;font-size: 1.2rem;">スイムラブスコア</span>
        <img style="position: absolute;bottom: 1.5rem;color: white;font-weight: bold;left: 1rem;font-size: 2rem; width: 32px; height: 32px;" :src="cardData.level" alt="">
        <span style="position: absolute;bottom: 1.2rem;color: white;font-weight: bold;left: 4rem;font-size: 1.2rem;">{{cardData.mark}}</span>
      </div>
      <div class="card-footer">
        <p style="color: #8293A3">総距離</p>
        <p style="color: #303235">1,000m</p>
        <p style="color: #8293A3">総時間</p>
        <p style="color: #303235">2h45m</p>
      </div>
    </div>
  </v-ons-page>
</template>

<script>
export default {
  data () {
    return {
      cardDatas: [
          {date: "03.17", day: "月", year: "2021", level: "static/assets/icons/C.png", mark: "50", img: "static/assets/images/practice01.png"},
          {date: "03.16", day: "月", year: "2021", level: "static/assets/icons/A.png", mark: "12", img: "static/assets/images/practice02.png"},
          {date: "03.15", day: "月", year: "2021", level: "static/assets/icons/A.png", mark: "50", img: "static/assets/images/practice03.png"},
          {date: "03.14", day: "月", year: "2021", level: "static/assets/icons/C.png", mark: "50", img: "static/assets/images/practice01.png"},
      ]
    }
  }
}
</script>

<style scoped>
  .page-title {
    padding-top: 2.5rem;
    background: white;
  }
  .page-title p {
    margin: 0;
    font-weight: bold;
    padding-bottom: 5px;
  }
  .card {
    border-radius: 10px;
    margin: 15px;
    padding: 0;
    overflow: hidden;
  }
  .card .card-body {
    position: relative;
  }
  .card .card-footer {
    display: flex;
    align-items: center;
  }
  .card .card-footer p {
    margin-left: 1rem;
  }
</style>
