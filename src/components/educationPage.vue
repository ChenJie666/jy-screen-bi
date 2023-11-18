<template>
  <div class="education_item">
    <!-- 设置插槽 -->
    <slot></slot>
  </div>
</template>

<script>
export default {}
</script>

<style lang="less">
.education_item {
  //height: 4.125rem;
  //flex-wrap: wrap;
  border: 1px solid blue;
  margin-left: .2rem;
  margin-right: .2rem;
  background-color: rgba(12, 130, 255, .85);
}
</style>