<template>
  <div class="home">
    <top-index></top-index>
    <sales-index></sales-index>
    <bottom-index></bottom-index>
    <map-index></map-index>
  </div>
</template>

<script setup lang="ts">
import TopIndex from '@/components/TopView/TopIndex.vue'
import BottomIndex from '@/components/BottomView/BottomIndex.vue'
import MapIndex from '@/components/MapView/MapIndex.vue'
import SalesIndex from '@/components/SalesView/SalesIndex.vue'
</script>

<style>
.home {
  width: 100%;
  height: 100%;
  padding: 20px;
  background: #eee;
  box-sizing: border-box;
}
</style>
