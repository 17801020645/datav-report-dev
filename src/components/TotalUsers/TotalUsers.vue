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
import { LineChart, CustomChart } from 'echarts/charts'
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
  CustomChart,
  TooltipComponent,
  ToolboxComponent,
  CanvasRenderer,
])

const option = ref({
  xAxis: {
    type: 'value',
    show: false,
  },
  yAxis: {
    type: 'category',
    data: [], //把两列数据合并到一起的关键设置
    show: false,
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
      data: [100],
      type: 'bar',
      stack: '总量',
      itemStyle: {
        color: '#45c946',
      },
    },
    {
      type: 'custom',
      data: [100],
      stack: '总量',
      renderItem: (
        param: echarts.CustomSeriesRenderItemParams,
        api: echarts.CustomSeriesRenderItemAPI,
      ) => {
        const value = api.value(0)
        const endPoint = api.coord([value, 0])
        return {
          type: 'group',
          position: endPoint,
          children: [
            {
              type: 'path',
              shape: {
                d: 'M1024 255.996 511.971 767.909 0 255.996 1024 255.996z',
                x: -5,
                y: -20,
                width: 10,
                height: 10,
                layout: 'cover',
              },
              style: {
                fill: '#45c946',
              },
            },
            {
              type: 'path',
              shape: {
                d: 'M0 767.909l512.029-511.913L1024 767.909 0 767.909z',
                x: -5,
                y: 10,
                width: 10,
                height: 10,
                layout: 'cover',
              },
              style: {
                fill: '#45c946',
              },
            },
          ],
        }
      },
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

<style scoped>
.total-users-footer {
  display: flex;
  align-items: center;
  .month {
    margin-left: 10px;
  }
}
</style>
