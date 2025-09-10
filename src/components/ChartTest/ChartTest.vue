<template>
  <div ref="chartRef" style='height: 100%, width: 100%  '></div>
</template>

<script lang="ts" setup>
import * as echarts from 'echarts'
import { onMounted, ref, onBeforeUnmount } from 'vue'

const chartRef = ref<HTMLElement | null>(null)
let myChart: echarts.ECharts | null = null

onMounted(() => {
  if (chartRef.value) {
    myChart = echarts.init(chartRef.value)

    const option: echarts.EChartsOption = {
      xAxis: {
        type: 'category',
        data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
      },
      yAxis: {
        type: 'value',
      },
      series: [
        {
          data: [820, 932, 901, 934, 1290, 1330, 1320],
          type: 'line',
          smooth: true,
        },
      ],
    }

    myChart.setOption(option)
  }
})

onBeforeUnmount(() => {
  if (myChart) {
    myChart.dispose()
  }
})
</script>

<style lang="sass" scoped></style>
