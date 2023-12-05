<template>
  <div>
    <h2>各月度入离职</h2>
    <div class="chart" id="monthOverview">
      各月度入离职
    </div>
  </div>
</template>

<script>
import {inject, onMounted, reactive} from "vue"

export default {
  setup() {
    let $echarts = inject("echarts")
    let $axios = inject("axios")

    let chartData = reactive({})

    async function getState() {
      let data = await $axios("/monthOverview/data")
      chartData = data.data.data
    }

    onMounted(() => {
      let myEchart = $echarts.init(document.getElementById("monthOverview"))
      getState().then(() => {
        myEchart.setOption({
          tooltip: {
            trigger: 'axis',
            axisPointer: {
              type: 'shadow'
            }
          },
          legend: {
            data: ['入职', '离职']
          },
          toolbox: {
            show: true,
            orient: 'vertical',
            left: 'right',
            top: 'center',
            feature: {
              mark: {show: true},
              dataView: {show: true, readOnly: false},
              magicType: {show: true, type: ['line', 'bar', 'stack']},
              restore: {show: true},
              saveAsImage: {show: true}
            }
          },
          xAxis: [
            {
              type: 'category',
              axisTick: {show: false},
              // data: ['2012', '2013', '2014', '2015', '2016']
              data: chartData.months
            }
          ],
          yAxis: [
            {
              type: 'value'
            }
          ],
          series: [
            {
              name: '入职',
              type: 'bar',
              barGap: 0,
              // label: labelOption,
              emphasis: {
                focus: 'series'
              },
              data: chartData.in_nums
            },
            {
              name: '离职',
              type: 'bar',
              // label: labelOption,
              emphasis: {
                focus: 'series'
              },
              data: chartData.out_nums
            }
          ]
        })
      })
    })

    return {getState, chartData}
  }
}
</script>

<style>

</style>