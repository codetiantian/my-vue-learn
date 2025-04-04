<template>
  <div>
    控制开关：
    <el-switch v-model="selSwitch" @change="changeSwitch"/>
  </div>
  <div :id="eleId" class="echar-item"></div>
</template>

<script setup>
import { onMounted, defineProps, inject, watch, nextTick, ref } from 'vue'
import * as echarts from 'echarts'

let myChart

const selActive = inject('activeName')

const selSwitch = ref(false)

watch(selActive, async () => {
  // 等待 Vue 完成 DOM 更新
  // await nextTick()
  if (myChart) {
    nextTick(() => {
      myChart.resize()
    })
  }
})

const props = defineProps({
  eleId: {
    type: String
  }
})

const options = {
  color: [
    {
      type: 'radial',
      x: 0.5,
      y: 0.5,
      r: 1,
      colorStops: [
        { offset: 0, color: '#ff4500' }, // 内侧浅色
        { offset: 1, color: 'red' }  // 外侧深色
      ]
    },
    {
      type: 'radial',
      x: 0.5,
      y: 0.5,
      r: 1,
      colorStops: [
        { offset: 0, color: '#40835e' },
        { offset: 1, color: '#007947' }
      ]
    },
    {
      type: 'radial',
      x: 0.5,
      y: 0.5,
      r: 1,
      colorStops: [
        { offset: 0, color: '#50b7c1' },
        { offset: 1, color: '#00a6ac' }
      ]
    },
    {
      type: 'radial',
      x: 0.5,
      y: 0.5,
      r: 1,
      colorStops: [
        { offset: 0, color: '#f173ac' },
        { offset: 1, color: '#ea66a6' }
      ]
    },
    {
      type: 'radial',
      x: 0.5,
      y: 0.5,
      r: 1,
      colorStops: [
        { offset: 0, color: '#de773f' },
        { offset: 1, color: '#f36c21' }
      ]
    }
  ],
  tooltip: {
    trigger: 'item'
  },
  legend: {
    top: '0%',
    left: 'center'
  },
  series: [
    {
      name: 'Access From',
      type: 'pie',
      radius: ['40%', '70%'],
      avoidLabelOverlap: false,
      labelLine: {
        show: true
      },
      data: [
        { 
          value: 1048, 
          name: 'Search Engine'
        },
        { 
          value: 735, 
          name: 'Direct'
        },
        { 
          value: 580, 
          name: 'Email'
        },
        { 
          value: 484,
          name: 'Union Ads'
        },
        { 
          value: 300,
          name: 'Video Ads'
        }
      ]
    }
  ]
}

const showTooltip = () => {
  myChart.dispatchAction({
    type: 'showTip',
    seriesIndex: 0, // 指定系列索引
    dataIndex: 0    // 指定数据索引
  })
}

const hideTooltip = () => {
  myChart.dispatchAction({
    type: 'hideTip'
  })
}

const changeSwitch = () => {
  console.log(selSwitch.value)
  if (selSwitch.value) {
    showTooltip()
  } else {
    hideTooltip()
  }
}

onMounted(() => {

  console.log(props.eleId)

  const chartDom = document.getElementById(props.eleId)
  myChart = echarts.init(chartDom)
  myChart.setOption(options)


  // const originalSeries = options.series

  // myChart.on('legendselectchanged', (params) => {
  //   console.log(`params.name: ${params.name}`)
  //   const legendSelected = params.selected
  //   console.log(legendSelected)
  //   const series = myChart.getOption().series

  //   // 遍历所有系列，找出具有相同 stack 的系列并同步状态
  //   const updatedSeries = originalSeries.map(serie => {
  //     if ((params.name === 'Email' && serie.stack === 'Ad') || (params.name === 'Baidu' && serie.stack === 'Search Engine')) {
  //       return {
  //         ...series,
  //         data: legendSelected[params.name] ? serie.data : []
  //       }
  //     }
  //     return serie
  //   })

  //   // 更新图表选项
  //   myChart.setOption({ series: updatedSeries })
  // })
})

</script>

<style>
.echar-item {
  height: 300px;
}
</style>