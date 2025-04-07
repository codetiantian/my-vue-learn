<template>
  <div class="my-box">
    <!-- <CusTables /> -->
     <!-- <FileUpload /> -->
      <!-- <CusUpload />

      <CusTable /> -->
      <!-- <CusEchars1 /> -->
       <!-- <div>num的值为：{{ num }}</div>
       <button @click="addBtnClicked">点击增加</button>
       <EcharsCus :zsechartdata="requestData.indexmistoryList" />
       <MyCus @click="myCusBtnClicked" /> -->
       <cus-table-comp :columns="tableColumns" :table-data="arrData" :scroll="{x: 500 }" />
  </div>
</template>

<script setup>
// import CusOne from './components/CusOne.vue'
// import CusTables from './components/CusTables.vue'
// import FileUpload from './components/FileUpload.vue'
// import CusUpload from './components/CusUpload.vue'
// import CusTable from './components/CusTable.vue'
// import CusEchars1 from './components/CusEchars1.vue'
// import EcharsCus from './components/EcharsCus.vue'
// import MyCus from './components/MyCus.vue'
import CusTableComp from './components/CusTableComp.vue'
import { ref } from 'vue'

// let num = 1

// const addBtnClicked = () => {
//   num++

//   console.log(num)
// }

// const myCusBtnClicked = () => {
//   console.log('myCusBtnClicked')
// }
// const data = {
//     dataColumnNameList: ['3月', '4月', '5月', '6月'],
//     rowDataList: [
//       {
//         rowName: '合同11212',

//         cellDataListInRow: [
//           {
//             columnName: '3月',

//             cellValue: '401.37元/s',

//             cellValueUnit: 'm/s',
//           },

//           {
//             columnName: '4月',

//             cellValue: '4.37元/s',

//             cellValueUnit: 'm/s',
//           },

//           {
//             columnName: '5月',

//             cellValue: '41.37元/s',

//             cellValueUnit: 'm/s',
//           },
//         ],
//       },

//       {
//         rowName: '合同2',

//         cellDataListInRow: [
//           {
//             columnName: '4月',

//             cellValue: '41.37元/s',

//             cellValueUnit: 'm/s',
//           },

//           {
//             columnName: '5月',

//             cellValue: '41.37元/s',

//             cellValueUnit: 'm/s',
//           },
//           {
//             columnName: '6月',

//             cellValue: '41.37元/s',

//             cellValueUnit: 'm/s',
//           },
//         ],
//       },

//       {
//         rowName: '合同3',

//         cellDataListInRow: [
//           {
//             columnName: '3月',

//             cellValue: '40.37元/s',
//           },

//           {
//             columnName: '4月',

//             cellValue: '41.37元/s',

//             cellValueUnit: 'm/s',
//           },

//           {
//             columnName: '5月',

//             cellValue: '41.37元/s',

//             cellValueUnit: 'm/s',
//           },
//         ],
//       },
//     ],
//   }

//   const newData = {}
//   const { dataColumnNameList, rowDataList } = data
//   newData.dataColumnNameList = dataColumnNameList.slice(0, 3)
//   newData.dataColumnNameList.map(item => {
//     rowDataList.find()
//   })

// const requestData = {
//   indexmistoryList: [{ indexprice: '1' }, { indexprice: '2' }, { indexprice: '8' }]
// }

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
