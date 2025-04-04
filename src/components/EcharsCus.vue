<!--
  * @Description: 
-->

<template>
  <div ref="lineChartRef" class="chart" style="width: 100px; height: 30px"></div>
  <!-- <echarts
    :option="option as any"
    width="150"
    :height="130"
    style="border: 1px solid transparent" /> -->
</template>

<script setup name="Gauge">
import { ref, defineProps, onMounted } from 'vue'
import * as echarts from 'echarts'
const props = defineProps({
  zsechartdata: {
    type: Object,
    required: true,
  },
  colorvalue: {
    type: Number,
    required: true,
  },
})
const lineChartRef = ref(null)
let lineChart
// 配置项
const option = ref({
  grid: {
    top: 1,
    right: 1,
    bottom: 1,
    left: 1,
    containLabel: false,
  },
  xAxis: {
    type: 'category',
    boundaryGap: false,
    show: false
  },
  yAxis: {
    type: 'value',
    show: false,
    boundaryGap: [0, '20%'],
  },
  visualMap: {
    type: 'piecewise',
    show: false,
    dimension: 0,
    seriesIndex: 0,
    pieces: [
      {
        gt: 1,
        lt: 7,
        color: 'rgba(255, 0, 0, 0.4)', // 为 1 < x < 3 的区域设置颜色
      }
    ],
  },
  series: [
    {
      type: 'line',
      smooth: 0.9,
      symbol: 'none',
      lineStyle: {
        color: 'rgba(255, 0, 0, 0.5)',
        width: 1,
      },
      areaStyle: {
        // 设置渐变色，模拟在特定区间下方有颜色
        color: {
          type: 'linear',
          x: 0,
          y: 0,
          x2: 0,
          y2: 1.2,
          colorStops: [
            { offset: 0, color: 'rgba(255, 0, 0, 0.3)' },
            { offset: 0.5, color: 'rgba(255, 0, 0, 0)' },
          ],
          global: false,
        },
      },
      data: [
        ['1', 2],
        ['2', 3],
        ['3', 6]
      ]
    },
  ],
})
function getEcharsData() {
  const arrEchars = []
  props.zsechartdata.forEach((item, index) => {
    arrEchars.push([`${index + 1}`, Number(item.indexprice)])
  })

  return arrEchars
}
onMounted(() => {
  console.log('---------------------------------------jkjkjjj', props.zsechartdata)
  option.value.series[0].data = getEcharsData(props.zsechartdata)
  // option.value.series[0].data = props.zsechartdata
  console.log(option.value.series[0].data)
  console.log(props.colorvalue)
  if (props.colorvalue > 0) {
    option.value.series[0].lineStyle.color = 'rgba(255, 0, 0, 0.5)'
    option.value.series[0].areaStyle.color.colorStops = [
      { offset: 0, color: 'rgba(255, 0, 0, 0.3)' },
      { offset: 0.5, color: 'rgba(255, 0, 0, 0)' },
    ]
  } else if (props.colorvalue == 0) {
    option.value.series[0].lineStyle.color = '#F09918'
    option.value.series[0].areaStyle.color.colorStops = [
      { offset: 0, color: 'rgba(240, 153, 24, 1)' },
      { offset: 0.5, color: 'rgba(240, 153, 24, 0)' },
    ]
  } else {
    option.value.series[0].lineStyle.color = '#28ADA7'
    option.value.series[0].areaStyle.color.colorStops = [
      { offset: 0, color: 'rgba(40, 173, 167, 1)' },
      { offset: 0.5, color: 'rgba(40, 173, 167, 0)' },
    ]
  }
  lineChart = echarts.init(lineChartRef.value)
  lineChart.setOption(option.value)
  //    const myChart = echarts.init(lineChartRef.value);
  //     myChart.setOption(option.value);
  //   console.log(option.value.series[0].data[0].value)
})
</script>
<style lang="less" scoped>
#echarts {
  position: relative;
  top: -20px;
}
</style>
