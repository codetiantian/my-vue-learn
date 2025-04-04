<template>
  <div>
    <!-- <CusTables /> -->
     <!-- <FileUpload /> -->
      <!-- <CusUpload />

      <CusTable /> -->
      <!-- <CusEchars1 /> -->
       <div>num的值为：{{ num }}</div>
       <button @click="addBtnClicked">点击增加</button>
       <EcharsCus :zsechartdata="requestData.indexmistoryList" />
       <MyCus @click="myCusBtnClicked" />
  </div>
</template>

<script setup>
// import CusOne from './components/CusOne.vue'
// import CusTables from './components/CusTables.vue'
// import FileUpload from './components/FileUpload.vue'
// import CusUpload from './components/CusUpload.vue'
// import CusTable from './components/CusTable.vue'
// import CusEchars1 from './components/CusEchars1.vue'
import EcharsCus from './components/EcharsCus.vue'
import MyCus from './components/MyCus.vue'

let num = 1

const addBtnClicked = () => {
  num++

  console.log(num)
}

const myCusBtnClicked = () => {
  console.log('myCusBtnClicked')
}
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

const requestData = {
  indexmistoryList: [{ indexprice: '1' }, { indexprice: '2' }, { indexprice: '8' }]
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
</style>
