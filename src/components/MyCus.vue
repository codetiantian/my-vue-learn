<template>
  <div>
    <button @click.stop="addBtnClicked">点击增加</button>
    <div>
      我就是试试
    </div>
  </div>
</template>
<script setup>
  const addBtnClicked = () => {
    console.log('addBtnClicked')
  }
</script>
