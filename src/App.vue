<template>
  <div class="my-box">
    <cus-table-comp 
      :columns="tableColumns" 
      :table-data="arrData" 
      :scroll="{ x: 800 }" 
      :style="{ width: '500px' }"
    />
    <div v-if="ipAddress">获取的ip为：{{ ipAddress }}</div>
    <div v-else>获取失败的原因为：{{ errMsg }}</div>
  </div>
</template>

<script setup>

import CusTableComp from './components/CusTableComp.vue'
import { ref, onMounted } from 'vue'
import axios from 'axios'

const ipAddress = ref('')
const errMsg = ref('')

const tableColumns = [
  {
    title: '交付月',
    key: 'month',
    width: 100,
    fixed: true
  },
  {
    title: 'JCC',
    key: 'jcc',
    unit: 'USD/BBL',
    children: [
      {
        title: '买',
        key: 'buy',
      },
      {
        title: '卖',
        key: 'sale',
      }
    ]
  },
  {
    title: 'LNG价格',
    key: 'lng',
    unit: '元/吨',
    children: [
      {
        title: '买',
        key: 'buy',
      },
      {
        title: '卖',
        key: 'sale',
      }
    ]
  },
  {
    title: 'PNG价格',
    key: 'png',
    unit: '元/方',
    children: [
      {
        title: '买',
        key: 'buy',
      },
      {
        title: '卖',
        key: 'sale',
      }
    ]
  }
] 

const arrData = ref([])

for (let i = 0; i < 8; i++) {
  arrData.value.push({
    month: `2025-0${i + 1}`,
    jcc: {
      buy: Math.random().toFixed(1),
      sale: Math.random().toFixed(1)
    },
    lng: {
      buy: Math.random().toFixed(1),
      sale: Math.random().toFixed(1)
    },
    png: {
      buy: Math.random().toFixed(1),
      sale: Math.random().toFixed(1)
    }
  })
}

const fetchIpAddress = async () => {
  try {
    // 使用公共 API 获取 IP 地址
    const response = await axios.get('https://api.ipify.org?format=json')
    ipAddress.value = response.data.ip

  } catch (error) {
    errMsg.value = error
  }
}

onMounted(() => {
  // 获取 IP 地址
  fetchIpAddress()
})

</script>

<style lang="less" scoped>
#main {
  height: 500px;
}

.demo-progress .el-progress--line {
  margin-bottom: 15px;
  max-width: 600px;
}

:deep(.el-progress-bar__inner) {
  position: static;
}
:deep(.el-progress-bar__innerText) {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
.my-box {
  width: 100vw;
  padding: 10px;
  box-sizing: border-box;
}
</style>

<style>
body {
  margin: 0;
  padding: 0;
}
</style>
