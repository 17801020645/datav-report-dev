<!--
该示例创建了一个可复用网格组件，并结合外部数据使用它。
-->

<script setup lang="ts">
import VChart from './GridView.vue'
import { ref } from 'vue'

const height = ref('100%')
const width = ref('100%')
const option = ref({
  xAxis: {
    type: 'category',
    boundaryGap: false,
    data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
  },
  yAxis: {
    type: 'value',
  },
  series: [
    {
      data: [820, 932, 901, 934, 1290, 1330, 1320],
      type: 'line',
      areaStyle: {},
    },
  ],
})
</script>

<template>
  <VChart :option="option" :width="width" :height="height"> </VChart>
</template>
