<template>
  <el-table
    :data="tableData"
    border
    style="width: 100%"
    :span-method="objectSpanMethod">
    <el-table-column prop="stats" label="属性" fixed width="100" />
    <el-table-column prop="type" label="类别" fixed width="150" />
    <el-table-column prop="date" label="日期" fixed width="120" />
    <el-table-column v-for="item in totalDay" :key="item" width="180">
      <template #header>
        <span>{{ item }}</span>
      </template>
      <template #default="scope">
        <el-input v-if="tableData[scope.$index].arrDaySet[item - 1].isShowInput" v-model="tableData[scope.$index].arrDaySet[item - 1].inputVal" placeholder="请输入" />
        <el-button v-else @click="editBtnClicked(tableData[scope.$index].arrDaySet[item - 1])">编辑</el-button>
      </template>
    </el-table-column>
  </el-table>

  <el-button @click="checkVal" style="margin-top: 20px;">查看值</el-button>
</template>

<script setup>
  import { onMounted, ref } from 'vue'
  import dayjs from 'dayjs'
  const tableData = ref(
    [
      {
        stats: '自有',
        type: '工况累积流量增量'
      },
      {
        stats: '自有',
        type: '标况累积流量增量'
      },
      {
        stats: '上游',
        type: '工况累积流量增量'
      },
      {
        stats: '上游',
        type: '标况累积流量增量'
      }
    ]
  )
  const totalDay = ref(0)

  const handleTableData = () => {
    const strCurMonth = dayjs().format('YYYY年MM月')
    totalDay.value = dayjs().daysInMonth()

    tableData.value.forEach(item => {
      item.date = strCurMonth
      item.arrDaySet = []
      for (let i = 0; i < totalDay.value; i++) {
        const curObj = {}
        curObj.strTitle = i + 1
        curObj.inputVal = ref('')
        curObj.isShowInput = ref(false)
        item.arrDaySet.push(curObj)
      }
    })
  }

  const objectSpanMethod = ({ rowIndex, columnIndex}) => { // 合并单元格
    if (columnIndex === 2) { // 合并日期
      if (rowIndex === 0) {
        return {
          rowspan: 4,
          colspan: 1
        }
      } else {
        return {
          rowspan: 0,
          colspan: 0,
        }
      }
    }
  }

  const editBtnClicked = (selObj) => {
    selObj.isShowInput = true
  }

  const checkVal = () => {
    console.log(tableData.value)
  }

  onMounted(() => {
    handleTableData()
  })

</script>