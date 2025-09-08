<template>
  <common-card title="今日交易用户数" value="81,014">
    <template #default>
      <v-chart class="chart" :option="option" autoresize />
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
import { use } from 'echarts/core'
import { CanvasRenderer } from 'echarts/renderers'
import { LineChart } from 'echarts/charts'
import {
  GridComponent,
  DatasetComponent,
  LegendComponent,
  TooltipComponent,
  ToolboxComponent,
} from 'echarts/components'
import VChart from 'vue-echarts'
import { ref } from 'vue'

use([
  DatasetComponent,
  GridComponent,
  LegendComponent,
  LineChart,
  TooltipComponent,
  ToolboxComponent,
  CanvasRenderer,
])

// provide(THEME_KEY, 'dark')

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

//TODO 按需引入，当前可行
// import { ref } from 'vue'
// import BaseChart from '../BaseChart/BaseChart.vue' // 根据你的路径调整

// const chartOption = ref({
//   xAxis: {},
//   yAxis: {},
//   series: [
//     {
//       type: 'line', // 使用折线图
//       data: [320, 432, 501, 334, 790, 930, 220, 320, 532, 320, 834, 690, 530],
//     },
//   ],
// })
</script>

<style scoped></style>
