<template>
    <form @submit.prevent="startUpload" v-el:form-upload-image>
        <div class="upload-btn-wrapper mx-4 my-4">
            <button class="btn">Upload Image</button>
            <input type="file" name="myfile" @change.prevent="selectImage" />
        </div>
    </form>
</template>

<script>

export default {
  data: function () {
    return {
      image: null  
      
    }
  },
  methods: {
    selectImage: function(e){
      // alert('masuk')
      // this.$emit('asdasd','test')
        // var formUpload = this.$els.formUploadImage
        // formUpload.submit()
        const file = e.target.files[0];
        this.image = URL.createObjectURL(file);
        alert(this.image)
    },
    startUpload: function(){
        alert('ini trigger dari onchange image')
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