<template>
  <el-upload
    v-model:file-list="fileList"
    class="upload-demo"
    action="api/upload.json"
    method="get"
    :with-credentials="true"
    multiple
    :on-preview="handlePreview"
    :on-remove="handleRemove"
  >
    <el-button type="primary">上传</el-button>
    <template #tip>
      <div class="el-upload__tip"> 
        文件上传，请选择
      </div>
    </template>
  </el-upload>

  <el-button style="margin-top: 20px;" @click="checkBtnClicked">查看</el-button>
</template>

<script setup>
import { ref } from 'vue'

const fileList = ref([])

const handleRemove = (file, uploadFiles) => {
  console.log(file, uploadFiles)
}

const handlePreview = (uploadFile) => {
  console.log(uploadFile)
}

const checkBtnClicked = () => {
  console.log(fileList.value)
}
</script>