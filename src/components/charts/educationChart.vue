<template>
  <div>
    <h2>学历比例</h2>
    <div class="chart" id="education">
      学历比例
    </div>
  </div>
</template>

<script>
import {inject, onMounted, reactive} from "vue"

export default {
  setup() {
    let $echarts = inject("echarts");
    let $axios = inject("axios")

    let chartData = reactive({})
    let pieData = reactive([])

    async function getState() {
      let data = await $axios({url: "/education/data"});
      chartData = data.data.data;
      let education = chartData.educations;
      let num = chartData.nums;

      education.forEach((e,index)=>{
        pieData.push({name:e,value:num[index]})
      })
      console.log(pieData)
    }

    onMounted(() => {
      let myEchart = $echarts.init(document.getElementById("education"));
      // 在运行时请求数据
      getState().then(() => {
        myEchart.setOption({
          legend:{
            top:"bottom"
          },
          series: [
            {
              name: 'Access From',
              type: 'pie',
              radius: '50%',
              data: pieData,
              // data: [
              //   { value: 1048, name: 'Search Engine' },
              //   { value: 735, name: 'Direct' },
              //   { value: 580, name: 'Email' },
              //   { value: 484, name: 'Union Ads' },
              //   { value: 300, name: 'Video Ads' }
              // ],
              emphasis: {
                itemStyle: {
                  shadowBlur: 10,
                  shadowOffsetX: 0,
                  shadowColor: 'rgba(0, 0, 0, 0.5)'
                }
              },
              itemStyle:{
                obrderRadius:10
              }
            }
          ]
        })
      })
    })
    return {getState,chartData,pieData}
  }
}
</script>

<style>
h2 {
  height: 0.5rem;
  color: #fff;
  line-height: 1rem;
  font-size: 0.25rem;
  text-align: center;
}
.chart{
  height: 4rem;
}
</style>