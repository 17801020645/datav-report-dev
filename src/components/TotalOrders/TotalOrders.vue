<template>
  <common-card title="累计订单量" value="2,157,420">
    <template #default>
      <v-chart class="chart" :option="option" autoresize />
    </template>
    <template #footer>
      <span>昨日订单量 </span>
      <span class="emphasis">2,000,000</span>
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
  xAxis: {},
  yAxis: {},
  series: [
    {
      type: 'line', // 使用折线图
      data: [320, 432, 501, 334, 790, 930, 220, 320, 532, 320, 834, 690, 530],
    },
  ],
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
