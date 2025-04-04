<template>
  <div class="container">
    <el-upload
      class="upload-demo"
      :http-request="handleHttpUpload"
      :on-success="uploadSuccess"
      :on-remove="handleRemove"
      :on-preview="handelpreview"
      drag
      :file-list="imageList"
      multiple
    >
      <el-icon class="el-icon--upload"><upload-filled /></el-icon>
      <div class="el-upload__text">Drop file here or <em>click to upload</em></div>
      <template #tip>
        <div class="el-upload__tip">jpg/png files with a size less than 500kb</div>
      </template>
    </el-upload>
  </div>
</template>
<script setup>
  import { ref } from "vue";
  import axios from 'axios'
  const imageList = ref([]);
  let aaa = ref("");
  /**
   * @description 图片上传
   * @param options upload 所有配置项
   * */
  const handleHttpUpload = async (options) => {
    let formData = new FormData();
    formData.append("file", options.file);
    try {
      const { data } = await axios.get('/api/upload.json', { params: formData });
      aaa.value = data;
    } catch (error) {
      options.onError(error);
    }
  };
  const uploadSuccess = async (data, file) => {
    file.response = aaa.value
    imageList.value.push(file);
    console.log(imageList.value);
  };

  const handleRemove = (uploadFile) => {
    const index = imageList.value.indexOf(uploadFile)
    if (index >= 0) {
      imageList.value.splice(index, 1)
    }
  }

  const handelpreview = async (val) => {
    const { url } = val.response.data
    window.open(url, "_blank")
  };
</script>
<style scoped lang="less">
.container {
  width: 100%;
  height: auto;
  img {
    width: calc(100% - 32px);
    margin-top: 16px;
    margin-left: 16px;
  }
}
</style>

