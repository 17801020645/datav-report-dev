<template>
  <common-card title="累计销售额" value="$ 32,039,165">
    <template #default>
      <div class="compare"></div>
    </template>
    <!-- 具名插槽 -->
    <template #footer>
      <div>
        <span>昨日销售额</span>
        <span class="money">$ 30,000,000</span>
      </div>
    </template>
  </common-card>
</template>

<script setup lang="ts">
import CommonCard from '../CommonCard/CommonCard.vue'
</script>

<style scoped>
.compare {
  background: yellow;
  height: 100%;
}
span {
  font-size: 12px;
}
.money {
  margin-left: 5px;
  color: #333;
  font-weight: 700;
}
</style>
