<template>
  <div id="cusEchars" class="echar-item"></div>
</template>

<script setup>
import { onMounted, inject, watch, nextTick } from 'vue'
import * as echarts from 'echarts'

let myChart

const selActive = inject('activeName')


watch(selActive, async () => {
  // 等待 Vue 完成 DOM 更新
  // await nextTick()
  if (myChart) {
    nextTick(() => {
      myChart.resize()
    })
  }
})

const options = {
  grid: {
    top: 1,
    right: 1,
    bottom: 1,
    left: 1,
    containLabel: false
  },
  xAxis: {
    type: 'category',
    boundaryGap: false,
    show: false
  },
  yAxis: {
    type: 'value',
    show: false,
    boundaryGap: [0, '30%']
  },
  visualMap: {
    type: 'piecewise',
    show: false,
    dimension: 0,
    seriesIndex: 0,
    pieces: [
      {
        gt: 0,
        lt: 5,
        color: 'rgba(255, 0, 0, 0.4)' // 为 1 < x < 3 的区域设置颜色
      }
    ]
  },
  series: [
    {
      type: 'line',
      smooth: 0.6,
      symbol: 'none',
      lineStyle: {
        color: '#5470C6',
        width: 1
      },
      areaStyle: {
        // 设置渐变色，模拟在特定区间下方有颜色
        color: {
          type: 'linear',
          x: 0,
          y: 0,
          x2: 0,
          y2: 1,
          colorStops: [
            { offset: 0, color: 'rgba(255, 0, 0, 0.5)' },
            { offset: 0.5, color: 'rgba(255, 0, 0, 0)' }
          ],
          global: false
        }
      },
      data: [
        ['2019-10-14', 10],
        ['2019-10-15', 300],
        ['2019-10-16', 10],
        ['2019-10-17', 40]
      ]
    }
  ]
}



onMounted(() => {
  const chartDom = document.getElementById('cusEchars')
  myChart = echarts.init(chartDom)
  myChart.setOption(options)
})

</script>

<style>
.echar-item {
  width: 150px;
  height: 30px;
}
</style>