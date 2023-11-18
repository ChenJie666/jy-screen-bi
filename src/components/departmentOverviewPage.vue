<template>
  <div class="department_overview_item">
    <!-- 设置插槽 -->
    <slot></slot>
  </div>
</template>

<script>
export default {}
</script>

<style lang="less">
.department_overview_item {
  //height: 4.125rem;
  //width: 12rem;
  border: 1px solid blue;
  margin-left: .2rem;
  //margin-right: .2rem;
  background-color: rgba(12, 130, 225, .85);
}
</style>