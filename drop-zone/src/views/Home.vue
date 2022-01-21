<template>
  <div class="home">
<h1>DropZone</h1>
    <DropZone @drop="handleDrop" @change="handleInput"/>
  <span class="file-info">File:{{dropzoneFile.name}}</span>
  </div>
</template>

<script>

import DropZone from '@/components/DropZone.vue'
import { ref } from '@vue/reactivity'

export default {
  name: 'Home',
  components: {
    DropZone
  },
  setup () {
    const dropzoneFile = ref('')
    const handleDrop = (e) => {
      dropzoneFile.value = e.dataTransfer.files[0]
    }

    const handleInput = () => {
      dropzoneFile.value = document.querySelector('#dropzoneFile').files[0]
    }

    return {
      dropzoneFile, handleDrop, handleInput
    }
  }
}
</script>

<style lang="scss" scoped>
.home{
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: #f1f1f1;

h1{
  font-size: 40px;
  margin-bottom: 32px;
}

.file-info{
  margin-top:32px;
}
}
</style>
