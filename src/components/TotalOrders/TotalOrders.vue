<template>
  <common-card title="累计订单量" value="2,157,420">
    <!-- <template> -->
    <!-- <div id="aaa" style="width: 100%; height: 100%"></div> -->
    <!-- <BaseChart :option="chartOption" style="width: 100%; height: 100%" /> -->
    <base-chart :option="chartOption" style="width: 100%; height: 100%"></base-chart>
    <!-- </template> -->
    <template #footer>
      <span>昨日订单量 </span>
      <span class="emphasis">2,000,000</span>
    </template>
  </common-card>
</template>

<script setup lang="ts">
import CommonCard from '../CommonCard/CommonCard.vue'

// import * as echarts from 'echarts'
// // 基于准备好的dom，初始化echarts实例
// const myChart = echarts.init(document.getElementById('aaa'))
// // 绘制图表
// myChart.setOption({
//   title: {
//     text: 'ECharts 入门示例',
//   },
//   tooltip: {},
//   xAxis: {
//     data: ['衬衫', '羊毛衫', '雪纺衫', '裤子', '高跟鞋', '袜子'],
//   },
//   yAxis: {},
//   series: [
//     {
//       name: '销量',
//       type: 'bar',
//       data: [5, 20, 36, 10, 10, 20],
//     },
//   ],
// })

import { ref } from 'vue'
import BaseChart from '../BaseChart/BaseChart.vue' // 根据你的路径调整

const chartOption = ref({
  xAxis: {},
  yAxis: {},
  series: [
    {
      type: 'line', // 使用折线图
      data: [320, 432, 501, 334, 790, 930, 220, 320, 532, 320, 834, 690, 530],
    },
  ],
})
</script>
