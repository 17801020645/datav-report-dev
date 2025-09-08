<template>
  <common-card title="累计订单量" value="2,157,420">
    <template #default>
      <!-- <div id="total-orders-chart" :style="'{ width: 100%, height: 100% }'"></div> -->
      <div>TODO</div>
    </template>
    <template #footer>
      <span>昨日订单量 </span>
      <span class="emphasis">2,000,000</span>
    </template>
  </common-card>
</template>

<script setup lang="ts">
import CommonCard from '../CommonCard/CommonCard.vue'
// import * as echarts from 'echarts'
// import { onMounted } from 'vue'

// onMounted(() => {
//   // 基于准备好的dom，初始化echarts实例
//   const myChart = echarts.init(document.getElementById('total-orders-chart'))

//   myChart.setOption({
//     xAxis: {},
//     yAxis: {},
//     series: [
//       {
//         type: 'line', // 使用折线图
//         data: [320, 432, 501, 334, 790, 930, 220, 320, 532, 320, 834, 690, 530],
//       },
//     ],
//   })
// })

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
