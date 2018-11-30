<template>
  <div>
    {{ imageurl }}
    <img class='resize' :src="imageUrl" alt="image">
  </div>
</template>

<script>
import { ipcRenderer } from 'electron';
export default {
    created() {
      ipcRenderer.on('image', (event, arg) => {
        this.imageUrl = arg
      })
    },
    data() {
      return {
        imageUrl: ''
      }
    }
  }
</script>
<style>
img.resize {
  height: 100%;
  width: 100%;
  margin:auto;
  display:block;
  object-fit:cover;
}
</style>
