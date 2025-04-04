<template>
  <el-table :data="tableData" border style="width: 100%">
    <el-table-column v-for="column in columns" :key="column.prop" :prop="column.prop" :label="column.label" />
  </el-table>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const columns = ref([]);
    const tableData = ref([]);
    const sourceData = {
      code: 200,
      msg: "[6acd7408]操作成功",
      data: {
"dataColumnNameList": [
    "声速",
    "流速",
    "效率因子",
    "电压增益(A)",
    "电压增益(B)",
    "增益极限值(A)",
    "增益极限值(B)"
],

"rowDataList": [

    {

        "rowName": "第一声道",

        "cellDataListInRow": [

            {

                "columnName": "声速",

                "cellValue": "401.37",

                "cellValueUnit": "m/s",

                "collectingTimestamp": "2024-12-19 14:23:00"

            },

            {

                "columnName": "流速",

                "cellValue": "15.00",

                "cellValueUnit": "",

                "collectingTimestamp": "2024-12-19 14:23:00"

            },

            {

                "columnName": "效率因子",

                "cellValue": "100.00",

                "cellValueUnit": "%",

                "collectingTimestamp": "2024-12-19 14:23:00"

            },

            {

                "columnName": "电压增益(A)",

                "cellValue": "2440.00",

                "cellValueUnit": "",

                "collectingTimestamp": "2024-12-19 14:23:05"

            },

            {

                "columnName": "电压增益(B)",

                "cellValue": "2336.00",

                "cellValueUnit": "",

                "collectingTimestamp": "2024-12-19 14:23:05"

            },

            {

                "columnName": "增益极限值(A)",

                "cellValue": "1868.00",

                "cellValueUnit": "",

                "collectingTimestamp": "2024-12-19 14:23:05"

            },

            {

                "columnName": "增益极限值(B)",

                "cellValue": "2162.00",

                "cellValueUnit": "",

                "collectingTimestamp": "2024-12-19 14:23:05"

            }

        ]

    },

    {

        "rowName": "第二声道",

        "cellDataListInRow": [

            {

                "columnName": "声速",

                "cellValue": "401.64",

                "cellValueUnit": "m/s",

                "collectingTimestamp": "2024-12-19 14:23:00"

            },

            {

                "columnName": "流速",

                "cellValue": "15.00",

                "cellValueUnit": "",

                "collectingTimestamp": "2024-12-19 14:23:00"

            },

            {

                "columnName": "效率因子",

                "cellValue": "100.00",

                "cellValueUnit": "%",

                "collectingTimestamp": "2024-12-19 14:23:00"

            },

            {

                "columnName": "电压增益(A)",

                "cellValue": "2473.00",

                "cellValueUnit": "",

                "collectingTimestamp": "2024-12-19 14:23:05"

            },

            {

                "columnName": "电压增益(B)",

                "cellValue": "2500.00",

                "cellValueUnit": "",

                "collectingTimestamp": "2024-12-19 14:23:05"

            },

            {

                "columnName": "增益极限值(A)",

                "cellValue": "2182.00",

                "cellValueUnit": "",

                "collectingTimestamp": "2024-12-19 14:23:05"

            },

            {

                "columnName": "增益极限值(B)",

                "cellValue": "2296.00",

                "cellValueUnit": "",

                "collectingTimestamp": "2024-12-19 14:23:05"

            }

        ]

    },

    {

        "rowName": "第四声道",

        "cellDataListInRow": [

            {

                "columnName": "声速",

                "cellValue": "401.56",

                "cellValueUnit": "m/s",

                "collectingTimestamp": "2024-12-19 14:23:00"

            },

            {

                "columnName": "流速",

                "cellValue": "15.00",

                "cellValueUnit": "",

                "collectingTimestamp": "2024-12-19 14:23:00"

            },

            {

                "columnName": "效率因子",

                "cellValue": "100.00",

                "cellValueUnit": "%",

                "collectingTimestamp": "2024-12-19 14:23:00"

            },

            {

                "columnName": "电压增益(A)",

                "cellValue": "2397.00",

                "cellValueUnit": "",

                "collectingTimestamp": "2024-12-19 14:23:05"

            },

            {

                "columnName": "电压增益(B)",

                "cellValue": "2401.00",

                "cellValueUnit": "",

                "collectingTimestamp": "2024-12-19 14:23:05"

            },

            {

                "columnName": "增益极限值(A)",

                "cellValue": "2211.00",

                "cellValueUnit": "",

                "collectingTimestamp": "2024-12-19 14:23:05"

            },

            {

                "columnName": "增益极限值(B)",

                "cellValue": "2161.00",

                "cellValueUnit": "",

                "collectingTimestamp": "2024-12-19 14:23:05"

            }

        ]

    },

    {

        "rowName": "第三声道",

        "cellDataListInRow": [

            {

                "columnName": "声速",

                "cellValue": "401.57",

                "cellValueUnit": "m/s",

                "collectingTimestamp": "2024-12-19 14:23:00"

            },

            {

                "columnName": "流速",

                "cellValue": "15.00",

                "cellValueUnit": "",

                "collectingTimestamp": "2024-12-19 14:23:00"

            },

            {

                "columnName": "效率因子",

                "cellValue": "100.00",

                "cellValueUnit": "%",

                "collectingTimestamp": "2024-12-19 14:23:00"

            },

            {

                "columnName": "电压增益(A)",

                "cellValue": "2581.00",

                "cellValueUnit": "",

                "collectingTimestamp": "2024-12-19 14:23:05"

            },

            {

                "columnName": "电压增益(B)",

                "cellValue": "2569.00",

                "cellValueUnit": "",

                "collectingTimestamp": "2024-12-19 14:23:05"

            },

            {

                "columnName": "增益极限值(A)",

                "cellValue": "2263.00",

                "cellValueUnit": "",

                "collectingTimestamp": "2024-12-19 14:23:05"

            },

            {

                "columnName": "增益极限值(B)",

                "cellValue": "2342.00",

                "cellValueUnit": "",

                "collectingTimestamp": "2024-12-19 14:23:00"

            }

        ]

    }
]
}
    };

    const processData = () => {
      const { dataColumnNameList, rowDataList } = sourceData.data;

      // 生成表头
      columns.value = [
        { label: "声道", prop: "rowName" },
        ...dataColumnNameList.map((columnName) => {
          const unit = rowDataList[0]?.cellDataListInRow.find((cell) => cell.columnName === columnName)?.cellValueUnit;
          return {
            label: unit ? `${columnName} (${unit})` : columnName,
            prop: columnName,
          };
        }),
      ];

      // 生成表格数据
      tableData.value = rowDataList.map((row) => {
        const rowData = { rowName: row.rowName };
        row.cellDataListInRow.forEach((cell) => {
          rowData[cell.columnName] = cell.cellValue;
        });
        return rowData;
      });
    };

    onMounted(() => {
      processData();
    });
</script>
