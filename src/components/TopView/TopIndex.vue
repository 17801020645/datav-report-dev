<template>
  <div class="top-view">
    <el-row :gutter="20">
      <el-col :span="6">
        <el-card shadow="always">
          <total-sales></total-sales>
        </el-card>
      </el-col>
      <el-col :span="6">
        <el-card shadow="always">
          <total-orders></total-orders>
        </el-card>
      </el-col>
      <el-col :span="6">
        <el-card shadow="always">
          <today-users></today-users>
        </el-card>
      </el-col>
      <el-col :span="6">
        <el-card shadow="always">
          <total-users></total-users>
        </el-card>
      </el-col>
    </el-row>
  </div>
</template>

<script setup lang="ts">
import TotalSales from '../TotalSales/TotalSales.vue'
import TotalOrders from '../TotalOrders/TotalOrders.vue'
import TodayUsers from '../TodayUsers/TodayUsers.vue'
import TotalUsers from '../TotalUsers/TotalUsers.vue'
</script>

<style scoped lang="scss"></style>
