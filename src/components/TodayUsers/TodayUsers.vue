<template>
  <common-card title="今日交易用户数" value="81,014">
    <template #default>
      <base-chart class="chart" :option="option" :width="width" :height="height" autoresize />
    </template>
    <!-- 具名插槽 -->
    <template #footer>
      <span>退货率 </span>
      <span class="emphasis">5.14%</span>
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
  color: ['#3398DB'],
  xAxis: {
    type: 'category',
    data: [
      '00:00',
      '01:00',
      '02:00',
      '03:00',
      '04:00',
      '05:00',
      '06:00',
      '07:00',
      '08:00',
      '09:00',
      '10:00',
      '11:00',
      '12:00',
      '13:00',
      '14:00',
    ],
    show: false,
  },
  yAxis: {
    // type: 'value',
    show: false,
  },
  series: [
    {
      data: [410, 82, 200, 334, 390, 330, 220, 150, 82, 200, 134, 290, 330, 150],
      type: 'bar',
      barWidth: '60%',
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
