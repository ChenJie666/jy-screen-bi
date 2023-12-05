<template>
  <div>
    <h2>部门入离职人数</h2>
    <div class="chart" id="departmentOverview">
      部门入离职人数
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

    async function getstate() {
      let data = await $axios("/departmentOverview/data")
      chartData = data.data.data
    }

    onMounted(() => {
      let myEchart = $echarts.init(document.getElementById("departmentOverview"))
      getstate().then(()=>{
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
              mark: { show: true },
              dataView: { show: true, readOnly: false },
              magicType: { show: true, type: ['line', 'bar', 'stack'] },
              restore: { show: true },
              saveAsImage: { show: true }
            }
          },
          xAxis: [
            {
              type: 'category',
              axisTick: { show: false },
              data: chartData.departments
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
              emphasis: {
                focus: 'series'
              },
              data: chartData.in_nums
            },
            {
              name: '离职',
              type: 'bar',
              emphasis: {
                focus: 'series'
              },
              data: chartData.out_nums
            },
          ]
        })
      })
    })

    return {getstate,chartData}
  }
}
</script>

<style>

</style>