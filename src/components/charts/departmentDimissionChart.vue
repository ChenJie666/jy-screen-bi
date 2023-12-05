<template>
  <div>
    <h2>各部门离职率</h2>
    <div class="chart" id="departmentDimission">
      各部门离职率
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
      let data = await $axios({url: "/departmentDimission/data"})
      chartData = data.data.data
    }

    onMounted(() => {
      let myEchart = $echarts.init(document.getElementById("departmentDimission"))
      //调用请求
      getState().then(() => {
        myEchart.setOption({
          tooltip: {
            trigger: 'axis',
            axisPointer: {
              type: 'shadow'
            }
          },
          grid: {
            top: "3%",
            left: "1%",
            right: "7%",
            bottom: "3%",
            containLabel: true
          },
          xAxis: {
            type: "value"
          },
          yAxis: {
            type: "category",
            data: chartData.departments
          },
          series: [
            {
              type: "bar",
              data: chartData.rates,
              itemStyle: {
                normal: {
                  barBorderRadius: [0, 5, 5, 0],
                  color: new $echarts.graphic.LinearGradient(0, 0, 1, 0,
                      [
                        {
                          offset: 0,
                          color: "#005eaa"
                        },
                        {
                          offset: 0.5,
                          color: "#339ca8"
                        },
                        {
                          offset: 1,
                          color: "#cda819"
                        }
                      ]
                  )
                }
              }
            }
          ]
        })
      })
    })

    return {getState,chartData}
  }
}
</script>

<style scoped>
.chart {
  height: 11rem;
}

h2 {
  height: 0.5rem;
  color: #fff;
  line-height: 1rem;
  font-size: 0.25rem;
  text-align: center;
}
</style>