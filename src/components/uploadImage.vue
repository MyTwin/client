<template>
    <div class="container d-flex justify-content-center">
      <form @submit.prevent="startUpload">
        <div class="upload-btn-wrapper mx-4 my-4">
            <button class="btn"><span class="glyphicon glyphicon-cloud-upload"></span> Upload Image</button>
            <input type="file" name="myfile" @change.prevent="selectImage" />
        </div>
      </form>
    </div>
</template>

<script>

import axios from 'axios'

export default {
  data: function () {
    return {
      image: null,
      animation: false 
    }
  },
  components: {
  },
  methods: {
    selectImage: function(e){
        // this.animation = true
        // alert(this.animation)
        $.blockUI({ message: '<h1><img src="busy.gif" /> Just a moment...</h1>' })
        const file = e.target.files[0];
        this.image = URL.createObjectURL(file);
        let formData = new FormData();
        formData.append('file', this.image);
        axios.post( 'http://localhost:3000/image/upload',
          formData,
          {
            headers: {
                'Content-Type': 'multipart/form-data'
            }
          }
        )
          .then(({data})=>{
            $.unblockUI()
            this.$emit('resultfromserver',data)
          })
          .catch( (err) => {
            $.unblockUI()
            // this.animation = false
            // alert(this.animation)
          });
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