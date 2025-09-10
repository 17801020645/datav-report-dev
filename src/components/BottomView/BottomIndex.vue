<template>
  <div class="bottom-view">
    <div class="view">
      <el-card shadow="hover">
        <template v-slot:header>
          <div class="title-wrapper">关键词搜索</div>
        </template>
        <template v-slot:default>
          <div class="chart-wrapper">
            <div class="chart-inner">
              <div class="chart">
                <div class="chart-title">搜索用户数</div>
                <div class="chart-data">93,634</div>
                <base-chart :option="searchUserOption" :width="width" :height="height">
                </base-chart>
              </div>
              <div class="chart">
                <div class="chart-title">搜索量</div>
                <div class="chart-data">198,782</div>
                <base-chart :option="searchUserOption" :width="width" :height="height"></base-chart>
                <!-- <v-chart :option="searchNumberOption"></v-chart> -->
              </div>
            </div>

            <div class="table-wrapper">
              <el-table :data="tableData">
                <el-table-column prop="rank" label="排名" width="180"></el-table-column>
                <el-table-column prop="keyword" label="关键词" width="180"></el-table-column>
                <el-table-column prop="count" label="总搜索量" width="180"></el-table-column>
                <el-table-column prop="users" label="搜索用户数" width="180"></el-table-column>
              </el-table>
              <el-pagination
                layout="prev, pager, next"
                :total="100"
                :hide-on-single-page="switchPagination"
                :page-size="4"
                background
                @current-change="onPageChange"
              />
            </div>
          </div>
        </template>
      </el-card>
    </div>
    <div class="view">
      <el-card shadow="hover">
        <template v-slot:header>
          <div class="title-wrapper">
            <div class="title">分类销售排行榜</div>
            <div class="radio-wrapper">
              <el-radio-group v-model="radioSelect" size="small">
                <el-radio-button label="品类"></el-radio-button>
                <el-radio-button label="商品"></el-radio-button>
              </el-radio-group>
            </div>
          </div>
        </template>
        <template v-slot:default>
          <div class="chart-wrapper">
            <base-chart :option="categoryOptions" :width="width" :height="height"></base-chart>
          </div>
        </template>
      </el-card>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import BaseChart from '../BaseChart/BaseChart.vue'

const height = ref('100%')
const width = ref('100%')

const switchPagination = ref(false)

const searchUserOption = ref({
  xAxis: {
    type: 'category',
    boundaryGap: false,
  },
  yAxis: {
    show: false,
    min: 0,
    max: 300,
  },
  series: [
    {
      type: 'line',
      data: [100, 150, 200, 250, 200, 150, 100, 50, 100, 150],
      areaStyle: {
        color: 'rgba(95, 187,255,.5)',
      },
      lineStyle: {
        color: 'rgba(95, 187,255)',
      },
      itemStyle: {
        opacity: 0,
      },
      smooth: true,
    },
  ],
  grid: {
    top: 0,
    left: 0,
    bottom: 0,
    right: 0,
  },
})

function onPageChange(page: number) {
  console.log(page)
}

// const searchNumberOption = ref({})
const tableData = ref([
  { id: 1, rank: 1, keyword: '北京', count: 100, users: 90, range: '90%' },
  { id: 2, rank: 2, keyword: '北京', count: 100, users: 90, range: '90%' },
  { id: 3, rank: 3, keyword: '北京', count: 100, users: 90, range: '90%' },
  { id: 4, rank: 4, keyword: '北京', count: 100, users: 90, range: '90%' },
  { id: 5, rank: 5, keyword: '北京', count: 100, users: 90, range: '90%' },
  { id: 6, rank: 6, keyword: '北京', count: 100, users: 90, range: '90%' },
])

const radioSelect = ref<string>('品类')
const categoryOptions = ref({
  title: [
    {
      text: '品类分布',
      textStyle: {
        fontSize: 14,
        color: '#666',
      },
      left: 20,
      top: 20,
    },
  ],
  series: [
    {
      type: 'pie',
      data: [
        {
          legendname: '粉面粥店',
          value: 67,
          percent: '15.40%',
        },
        {
          legendname: '简餐便当',
          value: 97,
          percent: '22.30%',
        },
        {
          legendname: '汉堡披萨',
          value: 92,
          percent: '21.15%',
        },
      ],
      label: {
        normal: {
          show: true,
          position: 'outter',
          formatter: function (param: Object | Array<Object>) {
            console.log(param)
          },
        },
      },
    },
  ],
})

// function renderPieChart() {
//   const mockData = [
//     {
//       legendname: '粉面粥店',
//       value: 67,
//       percent: '15.40%',
//     },
//     {
//       legendname: '简餐便当',
//       value: 97,
//       percent: '22.30%',
//     },
//     {
//       legendname: '汉堡披萨',
//       value: 92,
//       percent: '21.15%',
//     },
//     // {
//     //   legendname: '粉面粥店',
//     //   value: 67,
//     //   percent: '15.40%',
//     // },
//     (categoryOptions.value = {}),
//   ]
// }
</script>

<style scoped lang="scss">
.bottom-view {
  display: flex;
  margin-top: 20px;
  .view {
    flex: 1;
    width: 50%;
    box-sizing: border-box;

    &:first-child {
      padding: 0 10px 0 0;
    }

    &:last-child {
      padding: 0 0 0 10px;
    }

    .title-wrapper {
      display: flex;
      align-items: center;
      height: 60px;
      box-sizing: border-box;
      border-bottom: 1px solid #eee;
      font-size: 14px;
      font-weight: 500;
      padding: 0 0 0 20px;

      .radio-wrapper {
        flex: 1;
        display: flex;
        justify-content: flex-end;
        padding-right: 20px;
      }
    }

    .chart-wrapper {
      display: flex;
      flex-direction: column;
      height: 452px;

      .chart-inner {
        display: flex;
        padding: 0 10px;
        margin-top: 20px;

        .chart {
          flex: 1;
          padding: 0 10px;

          .chart-title {
            color: #999;
            font-size: 14px;
          }

          .chart-data {
            font-size: 22px;
            color: #333;
            font-weight: 500;
            letter-spacing: 2px;
          }

          .v-chart {
            height: 50px;
          }
        }
      }
      .table-wrapper {
        flex: 1;
        margin-top: 20px;
        padding: 0 20px 20px;

        .el-pagination {
          display: flex;
          justify-content: flex-end;
          margin-top: 15px;
        }
      }
    }
  }
}
</style>
