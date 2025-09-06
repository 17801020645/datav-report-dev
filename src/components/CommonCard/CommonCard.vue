<template>
  <div class="common-card">
    <div class="title">{{ title }}</div>
    <div class="value">{{ value }}</div>
    <div class="chart">
      <slot></slot>
    </div>
    <div class="line"></div>
    <div class="total">
      <slot name="footer"></slot>
    </div>
  </div>
</template>

<script setup lang="ts">
interface Props {
  title: string
  value: string
}

const { title, value } = defineProps<Props>()
</script>

<style scoped lang="scss">
.title {
  font-size: 12px;
  color: #999;
}
.value {
  font-size: 25px;
  color: #000;
  margin-top: 5px;
  letter-spacing: 1px;
}
.chart {
  height: 50px;
  background: red;
}
.line {
  margin: 10px 0;
  border-top: 1px solid #eee;
}
.total {
  font-size: 12px;
  color: #666;
}
</style>
