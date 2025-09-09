<template>
  <div class="sales-view">
    <el-card shadow="hover">
      <template v-slot:header>
        <div class="menu-wrapper">
          <el-menu mode="horizontal" :default-active="activeIndex" @select="handleSelect">
            <el-menu-item index="1">销售额</el-menu-item>
            <el-menu-item index="2">访问量</el-menu-item>
          </el-menu>
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

watchEffect(() => console.log(activeIndex.value))

function handleSelect(key: string) {
  activeIndex.value = key
}
</script>

<style scoped lang="scss">
.sales-view {
  margin-top: 20px;
}
</style>
