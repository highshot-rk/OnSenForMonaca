<template>
  <div style="width: 100%">
    <apexchart type="line" height="350" :options="chartOptions" :series="series"></apexchart>
  </div>
</template>

<script>
export default {
  name: "apex-chart",
  data () {
    return {
      series: [{
          name: "Swim",
          data: [10, 41, 35, 51, 49, 62, 69, 91, 148]
      },{
          name: "Avg",
          data: [30, 30, 30, 30, 30, 30, 30, 30, 30]
      },],
      chartOptions: {
        chart: {
          height: 350,
          type: 'line',
          zoom: {
            enabled: false
          }
        },
        dataLabels: {
          enabled: false
        },
        stroke: {
          curve: 'straight'
        },
        title: {
          text: 'メニュー #1',
          align: 'left'
        },
        grid: {
          row: {
            colors: ['#f3f3f3', 'transparent'], // takes an array which will be repeated on columns
            opacity: 0.5
          },
        },
        xaxis: {
          categories: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep'],
        }
      },
    }
  }
}
</script>

<style>

</style>
