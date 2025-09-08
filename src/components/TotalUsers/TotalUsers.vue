<template>
  <common-card title="累计用户数" value="1,087,503">
    <template #default>
      <v-chart class="chart" :option="option" autoresize />
    </template>
    <!-- 具名插槽 -->
    <template #footer>
      <div class="total-users-footer">
        <span>日同比 </span>
        <span class="emphasis">8.73%</span>
        <div class="increase"></div>
        <span class="month">月同比 </span>
        <span class="emphasis">35.91%</span>
        <div class="decrease"></div>
      </div>
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

const option = ref({
  xAxis: {
    type: 'value',
  },
  yAxis: {
    type: 'category',
    data: [], //把两列数据合并到一起的关键设置
  },
  series: [
    {
      data: [250],
      type: 'bar',
      stack: '总量',
      barWidth: 10,
      itemStyle: {
        color: '#eee',
      },
    },
    {
      data: [200],
      type: 'bar',
      stack: '总量',
      itemStyle: {
        color: '#45c946',
      },
    },
  ],
})
</script>

<style scoped>
.total-users-footer {
  display: flex;
  align-items: center;
  .month {
    margin-left: 10px;
  }
}
</style>
