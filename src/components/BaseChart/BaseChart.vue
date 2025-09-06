<!-- components/BaseChart.vue -->
<template>
  <div ref="chartDom" :style="{ width: width, height: height }"></div>
</template>

<script setup lang="ts">
// 按需引入的核心模块和图表组件:cite[5]:cite[7]
import * as echarts from 'echarts/core' // 引入 echarts 核心模块
import { BarChart, LineChart, PieChart } from 'echarts/charts' // 引入所需的图表类型
import {
  TitleComponent,
  TooltipComponent,
  GridComponent,
  LegendComponent,
} from 'echarts/components' // 引入所需的组件
import { CanvasRenderer } from 'echarts/renderers' // 引入 Canvas 渲染器
import { ref, onMounted, onBeforeUnmount, watch } from 'vue'

// 注册必需的组件、图表和渲染器:cite[5]:cite[7]
echarts.use([
  TitleComponent,
  TooltipComponent,
  GridComponent,
  LegendComponent,
  BarChart,
  LineChart,
  PieChart,
  CanvasRenderer,
])

// 定义组件接收的属性
const props = defineProps({
  option: {
    // ECharts 配置选项
    type: Object,
    required: true,
    default: () => ({}),
  },
  width: {
    // 图表容器宽度
    type: String,
    default: '100%',
  },
  height: {
    // 图表容器高度
    type: String,
    default: '400px',
  },
  theme: {
    // 主题
    type: [String, Object],
    default: null,
  },
})

const chartDom = ref(null) // 引用图表容器 DOM
let chartInstance: echarts.ECharts | null = null

// 初始化图表
const initChart = () => {
  if (!chartDom.value) return
  // 如果已存在实例，先销毁:cite[8]
  if (chartInstance) {
    chartInstance.dispose()
  }
  // 初始化图表实例:cite[2]:cite[3]
  chartInstance = echarts.init(chartDom.value, props.theme)
  chartInstance.setOption(props.option)
}

// 监听选项变化，更新图表:cite[8]
watch(
  () => props.option,
  (newOption) => {
    if (chartInstance) {
      chartInstance.setOption(newOption)
    }
  },
  { deep: true },
) // 深度监听，因为 option 是对象

// 监听容器宽高变化，重置图表大小
const resizeChart = () => {
  if (chartInstance) {
    chartInstance.resize()
  }
}

onMounted(() => {
  initChart()
  // 添加窗口 resize 监听器，图表自适应:cite[8]
  window.addEventListener('resize', resizeChart)
})

onBeforeUnmount(() => {
  // 移除事件监听器
  window.removeEventListener('resize', resizeChart)
  // 销毁图表实例，释放资源:cite[8]
  if (chartInstance) {
    chartInstance.dispose()
    chartInstance = null
  }
})
</script>
