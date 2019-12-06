<template>
    <div class="container d-flex justify-content-center">
        <upload-image @sendImage="getImage"></upload-image>
    </div>
</template>

<script>

import uploadImage from './uploadImage'

export default {
  data: function () {
    return { 
      
    }
  },
  methods: {
    getImage(v) {
      this.$emit('getData', v)
    }
  },
  components: {
      uploadImage
  }
}
</script>

<style scoped>
  div {
      border: 5px;
  }
</style>