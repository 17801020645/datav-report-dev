<script setup lang="ts">
import { use } from 'echarts/core'
import { CanvasRenderer } from 'echarts/renderers'
import { LineChart, CustomChart } from 'echarts/charts'
import type { ECBasicOption } from 'echarts/types/dist/shared'
import {
  GridComponent,
  DatasetComponent,
  LegendComponent,
  TooltipComponent,
  ToolboxComponent,
} from 'echarts/components'
import VChart from 'vue-echarts'

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

interface Props {
  width: string
  height: string
  option: ECBasicOption | undefined
}

const { width = '100%', height = '100%', option = {} } = defineProps<Props>()
</script>

<template>
  <v-chart class="chart" :option="option" :style="{ width, height }" autoresize />
</template>

<style lang="sass" scoped></style>
