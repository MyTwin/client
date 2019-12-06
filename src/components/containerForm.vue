<template>
    <div class="container d-flex justify-content-center my-4" id="container-form">
        <upload-image @resultfromserver="resultFromServer"></upload-image>
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
    resultFromServer: function(data){
      this.$emit('resultfromserver',data)
      // alert(data)
    }
  },
  components: {
      uploadImage
  }
}
</script>

<style scoped>
  #container-form {
      border-style: dotted;
  }
</style>