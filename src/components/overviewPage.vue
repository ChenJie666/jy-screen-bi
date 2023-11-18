<template>
  <div class="overview_item">
    <!-- 设置插槽 -->
    <slot></slot>
  </div>
</template>

<script>
export default {}
</script>

<style lang="less">
.overview_item {
  height: 2.125rem;
  border: 1px solid blue;
  margin: .2rem;
  background-color: rgba(12,130,255,.85);
}
</style>