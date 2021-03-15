<template>
  <div class="container dark:bg-gray-700 flex flex-col shadow-lg pl-2 pt-2 h-full ml-12 border-b border-t border-gray-100 sm:rounded-lg">
    <h1 class="text-2xl text-gray-500 dark:text-gray-300">Why do you create a startup?</h1>
    <h5 class="text-2xl text-gray-300 dark:text-white mb-10">Trends</h5>
    <pie-chart
      :chartdata="chartdata"
      :options="options"
      style="position: relative; height:4.5rem; width:18rem; margin-left:2.6rem;"
      />
  </div>
</template>

<script>
import PieChart from './Chart.vue'

export default {
  name: 'PieChartContainer',
  components: { PieChart },
  props: {
    reports: Array,
  },
  data() {
    return {
    chartdata: null,
    options: {
        legend: {
            position: 'bottom',
            labels: {
                boxWidth: 10,
                usePointStyle: true,
                padding: 10,
                fontColor: "#a8a8a8",
            }
        }
    }
  }
  },
  created () {
      console.log(this.reports)
      this.chartdata = {
          datasets: [{
                backgroundColor:  [
                    '#E289F2',
                    '#855CF8',
                    '#503795',
                    '#B085FF'
                ],
                data: this.reports.map(report => report.total)
          }],
          labels: this.reports.map(report => report.category)
      }
  }
}
</script>