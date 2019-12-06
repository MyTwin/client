<template>
  <div class="upload-btn-wrapper mx-4 my-4">
  </div>
</template>

<script>

export default {
  data: function () {
    return {
      
    }
  },
  methods: {
    uploadImage: function(){
      // alert('masuk')
      this.$emit('asdasd','test')
    }
  }
}
</script>

<style scoped>
  .upload-btn-wrapper {
    position: relative;
    overflow: hidden;
    display: inline-block;
  }

  .btn {
    border: 2px solid gray;
    color: gray;
    background-color: white;
    padding: 8px 20px;
    border-radius: 8px;
    font-size: 20px;
    font-weight: bold;
  }

  .upload-btn-wrapper input[type=file] {
    font-size: 100px;
    position: absolute;
    left: 0;
    top: 0;
    opacity: 0;
  }
</style>