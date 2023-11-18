<template>
  <div class="month_overview_item">
    <!-- 设置插槽 -->
    <slot></slot>
  </div>
</template>

<script>
export default {}
</script>

<style lang="less">
.month_overview_item{
  height: 3.85rem;
  border: 1px solid blue;
  margin: .2rem;
  background-color: rgba(12,130,255,.85);
}
</style>