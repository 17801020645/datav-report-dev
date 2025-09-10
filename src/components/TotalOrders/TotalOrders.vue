<template>
  <common-card title="累计订单量" value="2,157,420">
    <template #default>
      <base-chart class="chart" :option="option" :width="width" :height="height" autoresize />
    </template>
    <template #footer>
      <span>昨日订单量 </span>
      <span class="emphasis">2,000,000</span>
    </template>
  </common-card>
</template>

<script setup lang="ts">
import CommonCard from '../CommonCard/CommonCard.vue'
import BaseChart from '../BaseChart/BaseChart.vue'
import { ref } from 'vue'

const height = ref('100%')
const width = ref('100%')

const option = ref({
  xAxis: {
    type: 'category',
    show: false,
    boundaryGap: false,
  },
  yAxis: {
    show: false,
  },
  series: [
    {
      type: 'line', // 使用折线图
      data: [320, 432, 501, 334, 790, 930, 220, 320, 532, 320, 834, 690, 530],
      areaStyle: {
        color: 'purple',
      },
      lineStyle: {
        width: 0,
      },
      itemStyle: {
        opacity: 0,
      },
      smooth: true,
    },
  ],
  grid: {
    top: 0,
    bottom: 0,
    left: 0,
    right: 0,
  },
})
</script>

<style scoped></style>
