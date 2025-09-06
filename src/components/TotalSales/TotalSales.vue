<template>
  <common-card title="累计销售额" value="$ 32,039,165">
    <template #default>
      <div class="compare-wrapper">
        <div class="compare">
          <span>日同比</span>
          <span class="emphasis">7.33%</span>
          <div class="increase"></div>
        </div>
        <div class="compare">
          <span>月同比</span>
          <span class="emphasis">7.33%</span>
          <div class="decrease"></div>
        </div>
      </div>
    </template>
    <!-- 具名插槽 -->
    <template #footer>
      <span>昨日销售额 </span>
      <span class="emphasis">$ 30,000,000</span>
    </template>
  </common-card>
</template>

<script setup lang="ts">
import CommonCard from '../CommonCard/CommonCard.vue'
</script>

<style scoped>
.compare-wrapper {
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  .compare {
    /* background: yellow; */
    display: flex;
    align-items: center;
    font-size: 12px;
    margin-top: 3px;
    color: #666;
  }
}
</style>
