<template>
<div @dragenter.prevent="toggleActive"
@dragleave.prevent="toggleActive"
@dragover.prevent
@drop.prevent="toggleActive"
:class="{'active':active}"
 class="dropzone">
<span>Drag or Drop File</span>
<span>OR</span>
<label for="dropzoneFile">Select File</label>
<input type="file" id="dropzoneFile"/>
</div>
</template>

<script>
import { ref } from '@vue/reactivity'
export default {
  name: 'DropZone',
  setup () {
    const active = ref(false)
    const toggleActive = () => {
      active.value = !active.value
    }
    return {
      active, toggleActive
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='scss' scoped>
.dropzone{
  width: 400px;
  height: 200px;
  border: 2px dashed #41b883;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  row-gap: 16px;
  background-color: #fff;
  transition: 0.3s ease all;

  label{
    background-color: #41b883;
    padding: 8px 12px;
    color: #fff;
    cursor: pointer;
    transition: 0.3s ease all;
  }
  input{
    display: none;
  }
}

.active{
  color: #fff;
  border-color:#fff ;
  background-color: #41b883;
  label{
    color: #41b883;
    background-color: #fff;
  }
}
</style>
