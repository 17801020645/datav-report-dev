<template>
  <div class="sales-view">
    <el-card shadow="hover">
      <template v-slot:header>
        <div class="menu-wrapper">
          <el-menu
            mode="horizontal"
            :default-active="activeIndex"
            @select="onMenuSelect"
            class="sales-view-menu"
          >
            <el-menu-item index="1">销售额</el-menu-item>
            <el-menu-item index="2">访问量</el-menu-item>
          </el-menu>
          <div class="menu-right">
            <el-radio-group v-model="radioSelect" size="small">
              <el-radio-button label="今日"></el-radio-button>
              <el-radio-button label="本周"></el-radio-button>
              <el-radio-button label="本月"></el-radio-button>
              <el-radio-button label="今年"></el-radio-button>
            </el-radio-group>
            <el-date-picker
              type="daterange"
              v-model="date"
              range-separator="至"
              start-placeholder="开始日期"
              end-placeholder="结束日期"
              size="small"
              unlink-panels
              :shortcuts="shortcuts"
              class="sales-view-date-picker"
            />
          </div>
        </div>
      </template>

      <div>222</div>
      <div>222</div>
      <div>444</div>

      <div>333</div>
    </el-card>
  </div>
</template>

<script setup lang="ts">
import { ref, watchEffect } from 'vue'

const activeIndex = ref<string>('1')
const radioSelect = ref<string>('今日')
const date = ref<unknown>()
const shortcuts = [
  {
    text: '最近一周',
    value: () => {
      const start = new Date()
      const end = new Date()
      start.setTime(start.getTime() - 3600 * 24 * 1000 * 7)
      return [start, end]
    },
  },
  {
    text: '最近一个月',
    value: () => {
      const start = new Date()
      const end = new Date()
      start.setTime(start.getTime() - 3600 * 24 * 1000 * 30)
      return [start, end]
    },
  },
  {
    text: '最近三个月',
    value: () => {
      const start = new Date()
      const end = new Date()
      start.setTime(start.getTime() - 3600 * 24 * 1000 * 90)
      return [start, end]
    },
  },
]

// TODO 用不到删除
watchEffect(() => console.log(activeIndex.value))
watchEffect(() => console.log(radioSelect.value))

function onMenuSelect(key: string) {
  activeIndex.value = key
}
</script>

<style scoped lang="scss">
.sales-view {
  margin-top: 20px;
  .menu-wrapper {
    position: relative;
    display: flex;
    .sales-view-menu {
      width: 100%;
      padding-left: 20px;
      .el-menu-item {
        height: 50px;
        line-height: 50px;
        margin: 0 20px;
      }
    }
    .menu-right {
      position: absolute;
      top: 5px;
      right: 20px;
      height: 50px;
      display: flex;
      align-items: center;
      gap: 20px;
      // flex-shrink: 0;
      // justify-content: flex-end;
      // .sales-view-date-picker {
      //   // width: 280px !important;
      //   margin-left: 20px;
      // }
    }
  }
}
</style>
