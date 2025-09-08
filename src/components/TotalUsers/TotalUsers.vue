<template>
  <common-card title="累计用户数" value="1,087,503">
    <template #default>
      <div>TODO</div>
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
