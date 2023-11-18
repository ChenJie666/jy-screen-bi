<template>
  <div>
    <header>
      <h1>人事流动分析图表</h1>
    </header>
    <section class="container">
      <section class="itemLeft">
        <overviewPage><overviewChart/></overviewPage>
        <section class="t">
          <departmentOverviewPage class="t1"><departmentOverviewChart/></departmentOverviewPage>
          <educationPage class="t2"><educationChart/></educationPage>
        </section>
        <monthOverviewPage><monthOverviewChart/></monthOverviewPage>
      </section>
      <section class="itemRight">
        <departmentDimissionPage><departmentDimissionChart/></departmentDimissionPage>
      </section>
    </section>
  </div>
</template>

<script>
import overviewPage from "@/components/overviewPage.vue"
import departmentOverviewPage from "@/components/departmentOverviewPage.vue"
import educationPage from "@/components/educationPage.vue"
import monthOverviewPage from "@/components/monthOverviewPage.vue"
import departmentDimissionPage from "@/components/departmentDimissionPage.vue"

import overviewChart from "@/components/charts/overviewChart.vue"
import departmentOverviewChart from "@/components/charts/departmentOverviewChart.vue"
import educationChart from "@/components/charts/educationChart.vue"
import monthOverviewChart from "@/components/charts/monthOverviewChart.vue"
import departmentDimissionChart from "@/components/charts/departmentDimissionChart.vue"

export default {
  components:{
    overviewPage,
    departmentOverviewPage,
    educationPage,
    monthOverviewPage,
    departmentDimissionPage,
    overviewChart,
    departmentOverviewChart,
    educationChart,
    monthOverviewChart,
    departmentDimissionChart
  }
}
</script>

<style lang="less">
header {
  height: 1rem;
  width: 100%;
  background-color: rgba(0, 0, 255, .1);
  //标题文字样式
  h1 {
    font-size: 0.375rem;
    color: #fff;
    text-align: center;
    line-height: 1rem;
  }
}

.container {
  min-width: 1200px;
  max-width: 2048px;
  margin: 0 auto;
  padding: .125rem .125rem 0;
  background-color: gray;
  display: flex;

  .itemLeft {
    flex: 3;
  }

  .itemRight {
    flex: 1;
  }

  .t {
    height: 4.125rem;
    margin: 0 auto;
    //padding: .125rem .125rem 0;
    background-color: gray;
    display: flex;
  }
  .t1 {
    flex:3
  }
  .t2 {
    flex:1
  }
}
</style>